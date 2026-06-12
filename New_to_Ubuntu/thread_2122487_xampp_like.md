---
title: "xampp like"
date: 2013-03-05
forum: New to Ubuntu
---

### Post by tendouser on 2013-03-05
Is any web app server like xampp for ubuntu ...i mean open source to be downloaded from the U S Center?

---

### Post by tendouser on 2013-03-05
[URL="http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/"]Install lamp with 1 command in Ubuntu 12.04, 12.10 Quantal Quetzal & LinuxMint13 | Unixmen

got it!

Thanks anyway!
[/URL]

---

### Post by slickymaster on 2013-03-05
Since you’re on Ubuntu you don’t have to install XAMPP to get a web server started. Why don’t you install the following packages, including all dependencies, in order:
[MySQL Community Server 5.5]("http://dev.mysql.com/downloads/mirror.php?id=412061")
[Apache 2.4.4]("http://httpd.apache.org/download.cgi#apache24")
[PHP 5.4.12]("http://www.php.net/get/php-5.4.12.tar.gz/from/a/mirror")

---

### Post by Lars Noodén on 2013-03-05
> **tendouser said:**
> [URL="http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/"]Install lamp with 1 command in Ubuntu 12.04, 12.10 Quantal Quetzal & LinuxMint13 | Unixmen

got it!

Thanks anyway!
[/URL]

That hops through some hoops with tasksel, which adds unneeded steps.  You really can get it with a single command:

```

sudo apt-get install lamp-server^

```

Note the caret ^ and welcome to Ubuntu

---

