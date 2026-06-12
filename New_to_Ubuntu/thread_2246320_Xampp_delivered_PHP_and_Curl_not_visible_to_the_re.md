---
title: "Xampp delivered PHP and Curl not visible to the rest of Ubuntu 14"
date: 2014-09-29
forum: New to Ubuntu
---

### Post by vincej on 2014-09-29
[COLOR=#333333][FONT=UbuntuRegular]I have installed a recent copy of XAMPP on Ubuntu 14.04.  I can see that PHP is enabled as I can do a Localhost and see through phpinfo() that Curl is enabled. 

So, I want to now install Composer for Laravel development

However, when I issue this command:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]curl -sS [https://getcomposer.org/installer](https://getcomposer.org/installer) | php[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I get the following error messages:[/FONT][/COLOR]

[LIST=1]
[*]The program 'curl' is currently not installed. You can install it by typing:
[INDENT]sudo apt-get install curl

The program 'php' is currently not installed. You can install it by typing:[/INDENT]
[*][INDENT]sudo apt-get install php5-cli[/INDENT]
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]So what gives, how do I make my implementation of curl and PHP not "visible" to the Ubuntu Kernal ?[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Thanks ![/FONT][/COLOR]

---

### Post by Lars Noodén on 2014-09-30
> **vincej said:**
> I get the following error messages

XAMPP was designed for Windows use.  It's by far not the easiest way to go in Ubuntu, nor in the other distros.  It sets up a parallel group of tools within the system and you will have trouble finding them and updating them.  If you are not in too deeply, I would propose installing a regular LAMP stack using the regular package manager instead.  That will give you not only an easier experience, including automated updates, it will make it easier for others here to help you since the programs will be where they are expected and you'l  be able to follow the regular tutorials and guides.  Again, same on other distros.  To set up LAMP, follow the instructions for removing XAMPP and then 
```

sudo apt-get update
sudo apt-get install lamp-server^
sudo apt-get install curl

```

Mind the caret, it is part of the meta-package name.  That wil get you Apache2, MySQL and PHP (and curl).  You already have GNU/Linux and there perl and python come as part of the normal kit.  You'll then find your default (first) virtual host's configuration file in /etc/apache2/sites-available/ and be able to start/stop Apache2 and MySQL just like any other daemon.

However, if you have to use XAMPP for some reason, then it will be work to set up and a certain time commitment to keep it up to date.  Even the security updates are not automatic for XAMPP.

---

### Post by vincej on 2014-09-30
Brilliant ! Worked a treat - however, now I am clueless on how to find phpinfo. How to start and stop the Lamp and where to put my HTML. sorry - just came over from Win7 !

---

### Post by Lars Noodén on 2014-09-30
> **vincej said:**
> Brilliant ! Worked a treat - however, now I am clueless on how to find phpinfo. How to start and stop the Lamp and where to put my HTML. sorry - just came over from Win7 !

Well, the web server can be started and stopped with [service](http://manpages.ubuntu.com/manpages/trusty/en/man8/service.8.html)

```

sudo service apache2 stop
sudo service apache2 start
sudo service apache2 restart

```

Same for MySQL.

Since you are on Ubuntu 14.04 LTS, the default location for your web pages will be in /var/www/html  That's for your default (first) virtual host.  The configuration file is /etc/apache2/sites/available/000-default.conf in case you decide you need to change something.  You'll have to restart apache2 for any changes to take effect.

About the web pages, if you are the only person on your server, you can take ownership of that directory so you can write it.  If you are sharing it, then more steps are needed.

```

sudo chown -R vincej:vincej /var/www/html/

```

You can put your php file with phpinfo() in it there.  phpinfo() is a function of php and goes in an html file.

---

