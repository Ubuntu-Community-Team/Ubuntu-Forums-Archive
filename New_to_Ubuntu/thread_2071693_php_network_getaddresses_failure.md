---
title: "php_network_getaddresses failure"
date: 2012-10-16
forum: New to Ubuntu
---

### Post by avatarum on 2012-10-16
Hello,
 
I have a PHP-programme accessing images in another domain. In order to position them correctly I need their dimensions. 
So I'll use the GD-functions to access them.
$im = createimagefromjpeg("[http://www.somesite.com/images/image.jpg](http://www.somesite.com/images/image.jpg)");
and then I manipulate the $im - result with other GD-function.
This worked on the server I was hosted on previously.
 
On my newly setup server it gives the following error though:
fopen([http://www.somesite.com/images/image.jpg](http://www.somesite.com/images/image.jpg)): failed to open stream: php_network_getaddresses: getaddrinfo failed: Temporary failure in name resolution in /var/www/bin/test.php on line 3
 
I''m an absolute newbe. I have setup the LAMP-server from DVD and only made changes to network/interfaces and the 000-default of apache to match my IP.
 
Can someone please tell me what to do?
 
Thanks,
Avatarum (Michel Ale)

---

