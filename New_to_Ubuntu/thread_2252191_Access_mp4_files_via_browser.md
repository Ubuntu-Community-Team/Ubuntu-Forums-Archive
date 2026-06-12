---
title: "Access mp4 files via browser"
date: 2014-11-10
forum: New to Ubuntu
---

### Post by Timaxusa on 2014-11-10
Hello everyone. Need help setting up access to my files via browser. Have to have an access to my mp4 files via http. Running nginx and wowza on ubuntu 12.04. Currently gives me [h=1]404 Not Found[/h]Please help. Thank you in advance

---

### Post by sandyd on 2014-11-10
> **Timaxusa said:**
> Hello everyone. Need help setting up access to my files via browser. Have to have an access to my mp4 files via http. Running nginx and wowza on ubuntu 12.04. Currently gives me [h=1]404 Not Found[/h]Please help. Thank you in advance

Hi, can you post your nginx config?

---

### Post by Timaxusa on 2014-11-10
Hi Sandyd,
 Here it go:
user www-data;
worker_processes 4;
pid /run/nginx.pid;


events {
    worker_connections 768;
    # multi_accept on;
}


http {


    ##
    # Basic Settings
    ##


    sendfile on;
    tcp_nopush on;
    tcp_nodelay on;
    keepalive_timeout 65;
    types_hash_max_size 2048;
    # server_tokens off;


    # server_names_hash_bucket_size 64;
    # server_name_in_redirect off;


    include /etc/nginx/mime.types;
    default_type application/octet-stream;


    ##
    # Logging Settings
    ##


    access_log /var/log/nginx/access.log;
    error_log /var/log/nginx/error.log;


    ##
    # Gzip Settings
    ##


    gzip on;
    gzip_disable "msie6";


    # gzip_vary on;
    # gzip_proxied any;
    # gzip_comp_level 6;
    # gzip_buffers 16 8k;
    # gzip_http_version 1.1;
    # gzip_types text/plain text/css application/json application/javascript text/xml application/xml application/xml+rss text/javascript;


    ##
    # Virtual Host Configs
    ##


    include /etc/nginx/conf.d/*.conf;
    include /etc/nginx/sites-enabled/*;
}


Everything else below is commented out so I did not include it.

---

### Post by nerdtron on 2014-11-10
Error 404 means file not found.

Are your files located inside the root directory of the website?

---

### Post by Timaxusa on 2014-11-10
Hi Nerdtron,
 No they are not. Files that I am trying to access are located in external harddrives that are mounted to /mount directory and there are a lot of different drives. How can I access them via browser? I figured that I need to somehow setup nginx to access them but not sure how... Any idea?

---

### Post by Timaxusa on 2014-11-11
Any help on this?

---

### Post by nerdtron on 2014-11-11
Not an expert here but I think you should move all your files in the root directory of nginx.

---

### Post by Timaxusa on 2014-11-11
No way I can do that. We are talking about 12 TB of data. I'm sure it's possible because I've seen it was done before but now I need it myself and no one knows...

---

### Post by nerdtron on 2014-11-11
You can move your entire website on the 12TB directory?

Or you can create another subdomain or virtual host with the root directory declared for the 12TB files. Then the link on the main domain can point to the subdomain. Be aware though, apparmor won't let you declare root directories that are not conventional i.e. not on system default folders.

---

### Post by Timaxusa on 2014-11-11
Hi Nerdtron,
 My setup is following: I am running VMWare Ubuntu with Wowza broadcaster and mp4 files are being recorded to attached storage devices. There are about 16 hard drives. Is this the only way to do it? Only on root folder?

---

### Post by SeijiSensei on 2014-11-12
Create symbolic links from the data storage devices to /var/www/html.  Make sure nginx is configured to allow symlinks.

---

### Post by sp40140 on 2014-11-12
On a side note, Have you tried any off the shelf tools to accomplish this? Something like Tonido?

---

### Post by darkapec on 2014-11-12
Not sure you are set on nginx but I have been able to do this via apache server. Then using chrome or firefox (with vlc plugin) or vlc directly, i am able to play videos over http. Everything from mp4 to avi files, all play without a hitch. If your interested in making a switch to apache I can send you some of my configs.

On second thought this should be very easy with nginx also... simply create loop back (BIND) mounts to /var/www (or where ever you have nginx set to share data from) folder. This should allow nginx to access all of the data on the drives without copying the data to the new location and because it is a filesystem mount you do not have to worry about symlinks.

---

### Post by Timaxusa on 2014-11-13
Thank you guy's! How can I [COLOR=#000000]configure nginx to allow symlinks?[/COLOR]

---

