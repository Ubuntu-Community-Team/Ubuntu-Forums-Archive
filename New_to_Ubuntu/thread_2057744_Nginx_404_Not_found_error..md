---
title: "Nginx 404 Not found error."
date: 2012-09-14
forum: New to Ubuntu
---

### Post by hitul007 on 2012-09-14
I am using ubuntu 12
I have installed nginx using 

**apt-get install nginx**

Now after installation i can easily found nginx start page on localhost.

After a restart i got not found 404 Not found error.

Now i again tried to configure it.

[h1]nginx.conf[/h1]
user www-data;
worker_processes 4;


events {
        worker_connections 768;
        # multi_accept on;
}

http {
        index index.html;

        server {
    listen 80;
    server_name mysite.com;
    index index.html;

    location /epg/ {
        #add_header name server_hitul;
        proxy_pass [http://192.168.0.116:80;](http://192.168.0.116:80;)
                }
        location /jj/ {
                add_header name1 hitul;
                proxy_pass [http://www.gmail.com;](http://www.gmail.com;)
                        }
        }
   Other fields
}

Now i have also configured another virtual host. Now my that configuration is 
in <b>sites-available</b> there exist my index.html file

in <b>sites-enabled</b> there exist mysite.com conf file which contains
server {
                listen 81;
                server_name mysite.com;
                index index.html;
        location /hi/ {
                proxy_pass [http://192.168.0.116;](http://192.168.0.116;)
                        }

        location /ok/ {
                proxy_pass [http://www.google.com;](http://www.google.com;)
                        }
        }

Now still i am getting 404 not found error. Also i have default from sites-enabled and site-available 
Now also there exist file index.html so now i'm getting error no 404 not found.

---

