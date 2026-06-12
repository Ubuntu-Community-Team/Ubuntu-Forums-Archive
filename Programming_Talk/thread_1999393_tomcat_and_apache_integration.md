---
title: "tomcat and apache integration"
date: 2012-06-08
forum: Programming Talk
---

### Post by prisha on 2012-06-08
hi
I am using tomcat application server (with 2 instances), apache webserver, load balancer.
ssl offloading is done at load balancer end i am not carrying it on webserver or application server 
I have an url [https://xyz.abc.net/](https://xyz.abc.net/).................................
which is functioned to open two windows one with a welcome page and other with a begin page of our apllication
I am getting a window welcome page, other window is coming  with a message "page cannot be displayed"
when i checked the url of the corresponding window i noticed its redirecting it to [http://xyz.abc.net/](http://xyz.abc.net/).................................

So i edited server.xml file by appending 
secure="true" and scheme="https" 
when i launch the url above process is repeating but URL of the window  with a message "page cannot be displayed"  is
[https://xyz.abc.net:80/](https://xyz.abc.net:80/).................................

If i edit both above urls properly by making http to https and by removing the port number application is launching properly

i am using two ports 8009 and 8010 for 2 tomcat instances, webserver is listening 8000 port
Please anyone help me in resolving the issue

---

