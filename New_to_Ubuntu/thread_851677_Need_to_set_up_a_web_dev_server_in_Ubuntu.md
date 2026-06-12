---
title: "Need to set up a web dev server in Ubuntu"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by noobydev on 2008-07-06
Hi, I'm a web designer and I need to setup a testing environment for a web application that I'm going to be working on.

I'm used to using Apache on Windows within Wampserver. This usually allows me to access a project by going to [http://localhost/project_name/](http://localhost/project_name/)

These are the intstructions I'm working with to set this all up:
[http://code.reddit.com/wiki/RedditStartToFinish](http://code.reddit.com/wiki/RedditStartToFinish)

Should I be using regular Ubuntu or the server edition?
How do I setup a local webserver in Ubuntu?
How do Install the dependencies listed in the link above?

Any help would be great!

Thanks.

---

### Post by scragar on 2008-07-06
easy install apache:
```
sudo apt-get install apache2
```

easy install dependencies:
```
sudo apt-get install build-essential python2.5-dev git-core subversion libpng12-0 libpng12-dev libjpeg62 libjpeg62-dev libfreetype6 libfreetype6-dev gettext memcached postgresql-8.2 libpq-dev curl
```then install the EasyIntall program with this guide:
[http://peak.telecommunity.com/DevCenter/EasyInstall#installing-easy-install](http://peak.telecommunity.com/DevCenter/EasyInstall#installing-easy-install)

and with that everything you will need will be installed.

---

### Post by lazyart on 2008-07-06
If you go with the server edition you can select a LAMP install and have Apache, MySQL and PHP up and running pretty quickly.

To get the dependencies, use:```
sudo apt-get install *package_1 package_2 package_3*
```or do them one at a time.  You will find that this setup will not install a gui.  If you need that (and don't be ashamed to admit it) then at the command prompt do```
sudo apt-get install ubuntu-desktop
```or kubuntu-desktop or even xubuntu-desktop.  Normally you don't put a gui on a server but if it's just for developing go for it.  If the desktop doesn't come up automatically when you start up, log into the command prompt and type```
startx
```Have fun!

---

### Post by Nano Geek on 2008-07-06
You should do a server install. It will ask you if you want to make it a LAMP (Linux, Apache, Mysql, PHP) installation. Check that box, and you're all set. 

By default, apache reads from the /var/www/ folder on your hard-drive. Note however that this does **not** install a GUI; just the command-line.

---

### Post by noobydev on 2008-07-06
Excellent replies. Thank you very much! :)

---

### Post by cariboo on 2008-07-07
There is a way easier way to install the lamp server packages. Just open a Application-->Accressories-->Terminal and type:

```
sudo tasksel
```

Use the arrow keys to move down to LAMP hit the space bar to select then tab to ok. Another window will pop up with a progress bar on it. It won't seem like it is doing anything for a while as it is downloading packages. When it starts to install the packages the progress bar will start to move. Just follow the instructions and you're done. To access your new apache2 server type:

```
http://localhost
```

You'll get a page that says It Works!

Jim

---

### Post by Lucid_3ntr0py on 2008-07-07
> **cariboo907 said:**
> There is a way easier way to install the lamp server packages. Just open a Application-->Accressories-->Terminal and type:

```
sudo tasksel
```

Use the arrow keys to move down to LAMP hit the space bar to select then tab to ok. Another window will pop up with a progress bar on it. It won't seem like it is doing anything for a while as it is downloading packages. When it starts to install the packages the progress bar will start to move. Just follow the instructions and you're done. To access your new apache2 server type:

```
http://localhost
```

You'll get a page that says It Works!

Jim

Hey, this is what I get:

xavier@xavier-desktop:~$ sudo tasksel
tasksel: aptitude failed (100)


Dunno what this means.hehe

---

### Post by mcduck on 2008-07-07
You can also do the same in Synaptic. Somewhere in the Menus is the option for "Mark Packages by task". Just use that, find the "LAMP server" and enable it.

You'll provbably want to install phmpyadmin as well.

---

