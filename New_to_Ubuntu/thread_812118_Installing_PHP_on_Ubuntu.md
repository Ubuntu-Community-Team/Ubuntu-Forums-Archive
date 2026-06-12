---
title: "Installing PHP on Ubuntu"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by kyalee on 2008-05-29
I'm trying to install PHP on ubuntu so I can preview my PHP files in my browser instead of having to upload them to my website.

First I

```
sudo apt-get install php5 libapache2-mod-php5
sudo apt-get install apache2
```

No problems, but Firefox still gives me a download dialog when I try to open Firefox. So the Ubuntu wiki suggests the following:

```
sudo a2enmod php5
```

This module is already inabled. Okay. So I try

```
sudo /etc/init.d/apache2 restart
```

No go. Ubuntu wiki tells me that this error: 

```
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

```

means there's a problem with apache, but I don't exactly understand how I'm supposed to fix it. Help?

---

### Post by Xerp on 2008-05-29
That last error is more of a warning. Its just saying that that ServerName hasn't been set so it uses a default :) You should see apache running anyway, and the default web page at [http://127.0.0.1](http://127.0.0.1)

[http://httpd.apache.org/docs/2.0/mod/core.html#servername](http://httpd.apache.org/docs/2.0/mod/core.html#servername)

---

### Post by furlabs on 2008-07-04
Xerp is right, the warning Apache is giving has nothing to do with your PHP problem.

Edit /etc/apache2/mods-available/mime.conf and uncomment the following line:
```
TypesConfig /etc/mime.types
```

If it was already uncommented, have a look in /etc/mime.types and make sure you see something like the following:
```

application/x-httpd-php                         phtml pht php
application/x-httpd-php-source                  phps
application/x-httpd-php3                        php3
application/x-httpd-php3-preprocessed           php3p
application/x-httpd-php4                        php4

```

Then restart apache.

---

### Post by Georgie.Mathews on 2008-07-04
IS it easier to install apache using the LAMP method on ubuntu server, or to do it manually?

---

### Post by cariboo on 2008-07-04
It is easier to install LAMP then it is to install individual packages. An easy way to install LAMP is to open a terminal and enter:

```
tasksel
```

This with bring up a menu, just select LAMP and then OK.

Jim

---

### Post by forger on 2008-07-04
> **kyalee said:**
> I'm trying to install PHP on ubuntu so I can preview my PHP files in my browser instead of having to upload them to my website.


I might be wrong, but I don't think you need an apache server to preview websites in php.

You could use just php5-cli:
```
sudo apt-get install php5-cli
```

You can then install any of the dependencies, i.e. php5-mysql (and use the mysql server on your host)

---

### Post by forger on 2008-07-04
Ok here's the extensive guide for running simple local php script files **without apache**:

Install the php5-cli and debianutils (for tempfile command)
```
sudo apt-get install php5-cli debianutils
```

Make a "converter" script:
```
echo -e '#!/bin/bash\nfile=`tempfile -d . -s .html`\necho "Creating file: $file"\nphp5 $1 > $file\nfirefox $file\necho "Press any key to delete the temporary html file or ctrl-c to stop this script and keep it"\nread\necho "Removing $file"\nrm $file' > $HOME/phpview.sh
chmod +x $HOME/phpview.sh
```

So now you have a php to html converter that will make a temporary html file (in the current directory) and run it in firefox.

Let's test it; Create a "hello world" php/html file:
```

cd $HOME/Desktop
echo '#!/usr/bin/php5
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" dir="ltr" lang="en">
<head><title>Moo</title></head>
<body><?php echo "Hello world!"; ?></body>
</html>' > hi.php
```

```
~/phpview.sh ./hi.php
```

:KS

---

### Post by sidrit on 2008-08-10
here's the entire lamp server on hardy.

[http://sidrit.wordpress.com/2008/08/03/lamp-linux-apache-mysql-php-server-on-ubuntu-804/]("http://sidrit.wordpress.com/2008/08/03/lamp-linux-apache-mysql-php-server-on-ubuntu-804/")

just a few steps, really.

---

