---
title: "Setting up local sandbox for LAMP development"
date: 2010-05-12
forum: Programming Talk
---

### Post by JMJ_coder on 2010-05-12
I'm venturing into web development and am looking at setting up a local sandbox to test things out and develop apps and customizations. The languages aren't the concern, it's the testing environment.

The things I would need installed and running locally
[INDENT]
Apache
MySQL
PostgreSQL
PHP
Python (it's already installed, but will Apache recognize it outright?)[/INDENT]


How do I work with multiple projects at once? Say one customizing Drupal and the other creating a site with Django? I'd like to code, commit, test, repeat -- through my local system.

---

### Post by Hannes Hochreiner on 2010-05-13
You could try [XAMPP]("http://www.apachefriends.org/en/xampp.html"). I don't know whether it does all the things you need it to do, but it seems to be a nice and self-contained package. I use it for developing and testing a Joomla project.

---

### Post by hannaman on 2010-05-13
> **JMJ_coder said:**
> 
How do I work with multiple projects at once? Say one customizing Drupal and the other creating a site with Django? I'd like to code, commit, test, repeat -- through my local system.

There are a couple ways of doing this.
The easiest way is just using the filesystem to separate the different projects into different directories under your DocumentRoot and access them like:
[http://localhost/drupal](http://localhost/drupal)
[http://localhost/django](http://localhost/django)

Apache supports virtual sites as well.  So each project could be setup within it own virtual site.  Examples of setting up virtual sites can be found on Apache's site at [http://httpd.apache.org/docs/2.0/vhosts/examples.html](http://httpd.apache.org/docs/2.0/vhosts/examples.html)

---

### Post by jbrice on 2010-05-13
I have been looking at this recently, and - an interesting approach is to run your choice of web sever as a virtualised install. 
Basic steps are:
1/ Install - say - VirtualBox to provide the virtual environmant.
2/ Install and set up your choice of server(s) as a virtual system.
3/ Set up a shared folder between the your "real" system and the virtual server system. Use this to connect your development system to the development files on the virtual server.

Seems to be loads of advantages in doing it this way: 
- very little chance of messing up your primary system when installing and configuring server stuff 
- easy to snapshot server configurations for roll-back and cloning server installs.
- as many independent and sand-boxed servers as you can fit on your hard disk.
- ready-rolled virtual servers available to install and have up and running in minutes - e.g. [http://www.turnkeylinux.org/lamp](http://www.turnkeylinux.org/lamp) (which is a ready-to-go Ubuntu LAMP server) or [http://www.turnkeylinux.org/drupal6](http://www.turnkeylinux.org/drupal6) (you did mention Drupal).

---

### Post by Shalaby on 2010-06-29
I am a web developer my self and i am using ubuntu for everything, the easiest way to setup suitable environment is goto the menu bar choose:
System > Administration > synaptic package manager
then from the menu bar up there choose :
Edit > Mark packages by task
then mark LAMP Server
after installing lamp, you will need phpmyadmin,simply run in the trminal
```
sudo apt-get install phpmyadmin
```
you can now put ur files in /var/www folder
and u can access the server from the browser by typing in the address bar of the browser
[http://localhost](http://localhost)
done.

---

