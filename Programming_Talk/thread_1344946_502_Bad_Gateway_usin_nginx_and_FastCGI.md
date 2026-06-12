---
title: "502 Bad Gateway usin nginx and FastCGI"
date: 2009-12-03
forum: Programming Talk
---

### Post by WinterWeaver on 2009-12-03
I'm hoping someone has experience with these.
Buildout manages my django and python sandbox, but also generates the nginx configuration file, and a wee start/stop script for fcgi.

After buildout runs, I create a symlink to the generated nginx config file, in the nginx sites-available and sites-enabled dirs.
Restarting nginx yields no errors.

Next I run the startup script (which runs the django runfcgi). The script runs without errors, but if I navigate to [http://localhost:8000/](http://localhost:8000/)  then I get a 502 Bad Gateway error.

The nginx log reveals the following error:
```
2009/12/03 19:18:48 [crit] 18036#0: *1 connect() to unix:/home/andre/Projects/AfrEco/buildout-afreco/bin/develop.sock failed (13: Permission denied) while connecting to upstream, client: 127.0.0.1, server: localhost, request: "GET /favicon.ico HTTP/1.1", upstream: "fastcgi://unix:/home/andre/Projects/AfrEco/buildout-afreco/bin/develop.sock:", host: "localhost:8000"
```This is develop.fcgi (this script starts the django fcgi server):
```
#!/bin/sh
 
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DESC="FastCGI "
NAME=develop
SCRIPTNAME=/etc/init.d/$NAME
 
ROOT=/home/andre/Projects/AfrEco/buildout-afreco
BIN_PATH=$ROOT/bin
LOG_PATH=$ROOT/log
CONTROLSCRIPT=$BIN_PATH/$NAME
PIDFILE=$BIN_PATH/$NAME.pid
SOCKET_FILE=$BIN_PATH/$NAME.sock
 
d_start(){
    if [ -f $PIDFILE ]; then
echo -n " already running"
    else
        $CONTROLSCRIPT runfcgi \
        method=threaded \
        socket=$SOCKET_FILE \
        errorlog=$LOG_PATH/develop_errors \
        pidfile=$PIDFILE
    fi
}
 
d_stop(){
    kill `cat $PIDFILE` \
            || echo -n " not running"
    if [ -f $PIDFILE ]; then
        rm -f $PIDFILE
    fi
}
 
 
case $1 in
    start)
    echo -n "Starting $DESC: $NAME"
    d_start
    echo "."
    ;;
    stop)
    echo -n "Stopping $DESC: $NAME"
    d_stop
    echo "."
    ;;
    restart)
    echo -n "Restarting: $DESC: $NAME"
    d_stop
    sleep 1
    d_start
    echo "."
    ;;
    *)
    echo "Usage: $0 (start|stop|restart)"
    exit 1
    ;;
esac
```nginx config file:
```
server {
    server_name localhost;
    listen 8000;
 
    location ^~ /media/static/ {
        alias /home/andre/Projects/AfrEco/buildout-afreco/src/afreco/media/static/;
        expires 31d;
    }
    
    location ^~ /media/content/ {
        alias /home/andre/Projects/AfrEco/buildout-afreco/content/develop/;
        expires 31d;
    }
    
    # django admin static resources
    location ^~ /media/admin/ {
        alias /home/andre/Projects/AfrEco/buildout-afreco/parts/develop/django/contrib/admin/media/;
        expires 31d;
    }
 
    # django fcgi
    location / {
        fastcgi_pass unix:/home/andre/Projects/AfrEco/buildout-afreco/bin/develop.sock;
        fastcgi_param REQUEST_METHOD $request_method;
        fastcgi_param QUERY_STRING $query_string;
        fastcgi_param CONTENT_TYPE $content_type;
        fastcgi_param CONTENT_LENGTH $content_length;
        fastcgi_param SERVER_PROTOCOL $server_protocol;
        fastcgi_param SERVER_PORT $server_port;
        fastcgi_param SERVER_NAME $server_name;
        fastcgi_param PATH_INFO $fastcgi_script_name;
        fastcgi_param SERVER_ADDR $server_addr;
    }
}
```As far as I can see this is a issue with user permissions. Since nginx runs as www-data, I added the www-data user to my personal users group, so in theory it should work. I've been battling with this all day and hope that someone is able to help.

---

