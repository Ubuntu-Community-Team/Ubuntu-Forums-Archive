---
title: "Seeking guidance in how to install and use wordpress"
date: 2020-07-12
forum: New to Ubuntu
---

### Post by wsfield99 on 2020-07-12
First off, please forgive me if this is posted in the wrong place.  I am trying to install WordPress under Ubuntu 20.04.  I followed the instructions in this link [https://linuxconfig.org/ubuntu-20-04-wordpress-with-apache-installation](https://linuxconfig.org/ubuntu-20-04-wordpress-with-apache-installation).  Once everything was installed and configured I opened my browser to 127.0.0.1 and received the following error message:  PHP installation appears to be missing the MySQL extension.  I've done Google searches on how to resolve the problems which has to do with outdated extensions, but I haven't found a solution that I can understand and follow.  Please let me know if there is any additional information I need to supply.  Thank you in advance.  Scott

---

### Post by SeijiSensei on 2020-07-12
You should install the lamp-server package

```
sudo apt install lamp-server^
```

The tilde ("^") is required.  If you install the package, you'll get all the little pieces that interconnect Apache, PHP, and MySQL.

You should then be able to unpack the WP .zip archive in the root of the directory you've designated as the location for the website.  By default it is /var/www/html, though you can change it to another directory if you have experience with Apache.  If not, stick with the default for the moment.  To install anything into /var/www/html you'll need to use "sudo" since that directory is owned by the "root" (administrative) user.

---

### Post by wsfield99 on 2020-07-12
Thank you.  I think this was exactly what I was looking for.  Scott

---

### Post by wsfield99 on 2020-07-13
Hello,  I've successfully installed lamp-server.  Would you please tell me where I can go for step by step instructions on where to go from here.  I have a webpage that I created with DreamWeaver and which is hosted by Arvixe.  My goal is to be able to update it using WordPress because the DreamWeaver software is way too expensive.  Thanks in advance and please let me know what additional information I need to share.  Scott

---

### Post by sdsurfer on 2020-07-13
Start here:

[https://wordpress.org/support/article/how-to-install-wordpress/](https://wordpress.org/support/article/how-to-install-wordpress/)

Dreamweaver is outdated anyway, I am always surprised people are still using it. You do need a decent IDE though, my first preference is PHP Storm but that is also costly. Netbeans is free and does nearly everything Storm does. Start here on setting up NetBeans:

[https://netbeans.org/community/releases/82/install.html](https://netbeans.org/community/releases/82/install.html)

You will probably encounter challenges installing Netbeans, mostly around getting Java to work properly. The second thing to watch for is Netbeans has several distributions tailored to languages - for example, it's different for Java or app development than PHP. You want to tailor your Netbeans install for PHP, HTML, and Javascript if you are going to be working with Wordpress.

Last, note that Wordpress is a web-based framework. I know you are probably referring to the usage of Dreamweaver to update the pages, but Wordpress is not a "replacement" for Dreamweaver. Netbeans would be though.

---

### Post by ActionParsnip on 2020-07-13
> **SeijiSensei said:**
> You should install the lamp-server package

```
sudo apt install lamp-server^
```

The tilde ("^") is required.  If you install the package, you'll get all the little pieces that interconnect Apache, PHP, and MySQL.

You should then be able to unpack the WP .zip archive in the root of the directory you've designated as the location for the website.  By default it is /var/www/html, though you can change it to another directory if you have experience with Apache.  If not, stick with the default for the moment.  To install anything into /var/www/html you'll need to use "sudo" since that directory is owned by the "root" (administrative) user.

"^" is a caret
[https://en.wikipedia.org/wiki/Caret](https://en.wikipedia.org/wiki/Caret)

"~" is a tilde
[https://en.wikipedia.org/wiki/Tilde](https://en.wikipedia.org/wiki/Tilde)

---

### Post by wsfield99 on 2020-07-14
Thanks for all of your help guys.  I appreciate your patience with me too.  Scott

---

### Post by SeijiSensei on 2020-07-14
> **ActionParsnip said:**
> "^" is a caret
[https://en.wikipedia.org/wiki/Caret](https://en.wikipedia.org/wiki/Caret)

"~" is a tilde
[https://en.wikipedia.org/wiki/Tilde](https://en.wikipedia.org/wiki/Tilde)

Oops.

---

