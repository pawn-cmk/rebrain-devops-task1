![image nginx](https://nginx.org/nginx.png)
[Что это!?](https://ru.wikipedia.org/wiki/Nginx) 

[Offical web site](https://www.nginx.com)

> Игорь Сысоев

# Настало время пояснительной записки

В данном репозитории находится конфигурационный файл nginx и ...

    Как заставить его работать (Для linux)
1. установка nginx [Дока](https://nginx.org/ru/docs/install.html) или 
    - под *DPKG* ``` sudo apt-get install nginx ```
    - под *RPM* ``` sudo yum install nginx ```
2. внутри уcтановленного ПО копируем файл в директорию *conf.d* c заменой 
> стандартный путь для linux **/etc/nginx/**
3. краткое описание по *nginx.conf*
4. краткое описание по командам

## краткое описание по *nginx.conf*

    Коротко о важном
- ```worker_processes  5;  ## Default: 1```
    - [MAN](http://nginx.org/ru/docs/ngx_core_module.html#worker_processes)
    - *простая рекомендация установки его равным числу свободых процессорных ядер* 
- ```worker_rlimit_nofile 8192;```
    - [MAN](http://nginx.org/ru/docs/ngx_core_module.html#worker_rlimit_nofile)
    - ** 
- ```worker_connections  4096;  ## Default: 1024```
    - [MAN](http://nginx.org/ru/docs/ngx_core_module.html#worker_connections)
    - *простая рекомендация* worker_rlimit_nofile = (worker_connections * worker_processes)*2 *и не забываем про лимиты(ulimit гугл в помощь, ман не резиновый) пользователя nginx* 
- ```include```
    - [MAN](http://nginx.org/ru/docs/ngx_core_module.html#include)
    - *включает другой файл* 
- ```location```
    - [MAN](https://nginx.org/ru/docs/http/ngx_http_core_module.html#location)
    - *Устанавливает конфигурацию в зависимости от URI запроса.*
- ```server_name```
    - [MAN](https://nginx.org/ru/docs/http/server_names.html)
    - *Добавляем DNS адреса под необходимый функционал*
- ```upstream```
    - [MAN](https://nginx.org/ru/docs/http/ngx_http_upstream_module.html)
    - *позволяет описывать группы серверов*
- ```proxy_pass```
    - [MAN](https://nginx.org/ru/docs/http/ngx_http_proxy_module.html#proxy_pass)
    - *Задаёт протокол и адрес проксируемого сервера*
- ```server```
    - [MAN](https://nginx.org/ru/docs/http/ngx_http_upstream_module.html#server)
    - *Задаёт адрес и другие параметры сервера*
- ```root```
    - [MAN](https://nginx.org/ru/docs/http/ngx_http_core_module.html#root)
    - *Задаёт корневой каталог для запросов*
    


## краткое описание по командам

> Запуск команд из под пользователя nginx(что врятли вы будете делать), либо из под пользователя с sudo.

- test the configuration file (рекомендация к использованию после изменений в конфигурационных файлах, дабы не положить балансировщик)
    - nginx -t
- START
    - service nginx start
    - systemctl start nginx
    - nginx start
- STOP
    - service nginx stop
    - systemctl stop nginx
    - nginx -s stop
- RELOAD (перечитать конфигурацию без остановки)
    - service nginx reload
    - systemctl reload nginx
    - nginx -s reload


