---
title: "Php"
date: 2011-11-21
forum: New to Ubuntu
---

### Post by 213Wayne on 2011-11-21
Hi 

I am attempting to install PHP software on my laptop (UBUNTU 10.04) using this command:
sudo sh /home/wayne/Desktop/install.sh

I get this  error:
wayne@ubuntu:~$ sudo sh /home/wayne/Desktop/php/install.sh
[sudo] password for wayne: 
Press the number:
1. Install PHP package
2. Uninstall PHP package
3. Exit.
1
[: 50: 1: unexpected operator
[: 50: 1: unexpected operator
[: 50: 1: unexpected operator
Press the number:
1. Install PHP package
2. Uninstall PHP package
3. Exit.

I'm not sure what the problem could be with the sh file.
Please assist.

go to [https://rapidshare.com/file/2572864370/install.sh](https://rapidshare.com/file/2572864370/install.sh) for the sh file.

---

### Post by mcduck on 2011-11-21
The link to the .sh file doesn't work, but I don't really see any reason why you'd want to use such script to install PHP anyway. The package manager will handle the job easily, and is definitely a more trustworthy method than any random script you'll find from the Web.

Here's a link to Ubuntu's server guide, to the page with instructions for PHP5: [https://help.ubuntu.com/11.04/serverguide/C/php5.html]("https://help.ubuntu.com/11.04/serverguide/C/php5.html"). And you'll probably want Apache as well: [https://help.ubuntu.com/11.04/serverguide/C/httpd.html]("https://help.ubuntu.com/11.04/serverguide/C/httpd.html")

And here's the short answer for installing PHP5:
For Apache:
```
sudo apt-get install php5 libapache2-mod-php5
```

..or standalone (for use without Apache):
```
sudo apt-get install php5 php5-cgi php5-cli
```

---

### Post by sadaruwan12 on 2011-11-21
You don't have to run a script to install PHP you can use the repo's to do that to install PHP you need to run a web server other wise you cant trouble shoot your web scripts that also is available in the repo's.[URL="https://help.ubuntu.com/community/ApacheMySQLPHP"]

Here's[/URL] a guide how to install a LAMP server in your computer.

And another [guide]("http://www.howtoforge.com/ubuntu_lamp_for_newbies").

Follow the first one it's easy and you don't have to do anything tasksel will take care of everything.

---

### Post by 213Wayne on 2011-11-21
Apologies for the late reply.

I actually need this specific install.sh file to install on my notebook.
I have purchased a product from a vendor and they have given me this file (install.sh). I want to actually upload PHP files onto the product using this app.

The support guys of this product don't have very good knowledge of Linux, so they are no help at all.
I need this actual file to work.
Can you configure the file to make it install on UBUNTU 10.04

---

### Post by satanselbow on 2011-11-21
As mcduck points out the rs link you supplied to the install.sh is broken.

Without seeing the contents of the file we don't stand a chance of fixing it :(

If it is not too long you could open it in a text editor and post it here between [code] tags ;)

Have you installed a lamp server / php on your local machine yet as even if we can fix the install.sh script it will not run without at least the php installation as listed before in this thread :)

---

### Post by 213Wayne on 2011-11-21
This is the contents of the install.sh file:

#!/bin/sh

while [ 1 ] ; do

echo Press the number:
echo 1. Install PHP package
echo 2. Uninstall PHP package
echo 3. Exit.

read A

if [ "$A" == "1" ] ; then
    echo Start to install PHP. Please wait ...
    killall httpd 2> /dev/null
    sleep 1
    if ! [ -d /home/php ]; then
        mkdir /home/php
    fi
    if ! [ -d /home/php/lib ]; then
        mkdir /home/php/lib
    fi
    cp -a ./lib/* /home/php/lib 2> /dev/null
    cp ./httpd.conf /etc/apache/conf/httpd.conf 2> /dev/null
    cp ./envvars /etc/apache/envvars 2> /dev/null
    cp -a ./php /etc/apache 2> /dev/null
    cp ./phpinfo.php /home/httpd/htdocs 2> /dev/null
    /etc/init.d/apache start
    echo PHP install sucess.
    break;
fi

if [ "$A" == "2" ] ; then
    echo Start to uninstall PHP. Please wait ...
    killall httpd > /dev/null
    sleep 1
    rm -fr /home/php 2> /dev/null
    rm -fr /etc/apache/php 2> /dev/null
    rm -f /home/httpd/htdocs/phpinfo.php 2> /dev/null
    cp ./httpd.conf.old /etc/apache/conf/httpd.conf 2> /dev/null
    cp ./envvars.old /etc/apache/envvars 2> /dev/null
    /etc/init.d/apache start
    echo PHP uninstall sucess.
    break;
fi

if [ "$A" == "3" ] ; then
    break;
fi

done

---

### Post by 213Wayne on 2011-11-21
I have installed Lamp server. Do I need to install Apache as well?

---

### Post by satanselbow on 2011-11-21
What is this actually meant to be installing? A php app? a php particular extension?

All it appears to do on first look is install php libraries which would most certainly be better done through the guides previously posted here as it is making a lot of incorrect assumptions about a default LAMP install on Ubuntu...

The script not working may actually be saving you a big headache!


Have you got a working apache (LAMP) installation already?

---

### Post by 213Wayne on 2011-11-21
How can I test if it works (Lamp server)?

---

### Post by SeijiSensei on 2011-11-21
If you installed Apache and PHP **from the repositories**, try this:

```
sudo echo '<?php phpinfo()?>' > /var/www/test.php
```

Now open a browser on the machine and trying viewing [http://localhost/test.php](http://localhost/test.php).  You should see the information page for PHP.

---

### Post by 213Wayne on 2011-11-22
Hi

So, according to you guys, Apache and lamp server should do the same task as the install.sh file.
Right?

---

### Post by 213Wayne on 2011-11-22
When I attempt to install the install.sh file using ./install.sh I get this:

Press the number:
1. Install PHP package
2. Uninstall PHP package
3. Exit.
1
Start to install PHP. Please wait ...
mkdir: cannot create directory `/home/php': Permission denied
mkdir: cannot create directory `/home/php/lib': No such file or directory
 * Starting web server apache2                                                  (13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]
PHP install sucess.

Why does it fail?

---

### Post by SeijiSensei on 2011-11-22
You need to run the script as root with sudo:

```
sudo ./install.sh
```

---

### Post by 213Wayne on 2011-11-23
Hi

I ran:
wayne@ubuntu:~$ sudo /etc/init.d/apache2 restart

and I got this:
/var/run/apache2.pid: 1: 1391: not found

What could be the problem?

---

