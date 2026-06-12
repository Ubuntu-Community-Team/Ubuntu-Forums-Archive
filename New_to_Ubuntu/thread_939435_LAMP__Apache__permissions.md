---
title: "LAMP / Apache / permissions"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by dESAI on 2008-10-05
Greetings good people,

Total noob alert!

I've installed LAMP on Desktop using the package installer. But for some reason I don't have rights to the folders where the site will be.

The folder I want access to is located in "/var/www/". 

I'm told the owner of the folder is "root". I tried switching user to root, via the desktop method, but none of my passwords were accepted.

I'm really frustrated now. I should be able to access these folders right?

Can someone please tell me how to do one of the following solutions:

1. Change the path of my site, so that localhost access a directory that I already have rights to.

2. Give myself rights to the directory /var/www/

I stress again that I'm not good (or happy) using the terminal. So I need the easiest solution and please feel free to dumb it down for me :)


Thanks all :D

D

---

### Post by zhuxiaonuan on 2008-10-05
:lolflag:














-----------------------
[ultrasound gel]("http://www.xinyangmed.net")

---

### Post by zephyrcat on 2008-10-06
There are a couple of things you can do:

1. Go to the terminal and type in:

sudo nautilus

This will open (after entering your password) nautilus, which is the file manager in Ubuntu as root. You will have to do this each time you want to write to the folder.

2. Follow step 1, then right click the www folder and choose properties and then permissions. From there, you can change the permissions. After this, you will be able to just use the regular file manager.

---

### Post by Primefalcon on 2008-10-06
actually you'd be better off typing gksudo nautilus. This way you won't mess up your permissions.

using sudo nautilus is how you may have messed up your permission sin the first place

---

### Post by bodhi.zazen on 2008-10-06
If you are wanting to run and modify apache I suggest you start with this :

[https://help.ubuntu.com/8.04/serverguide/C/httpd.html](https://help.ubuntu.com/8.04/serverguide/C/httpd.html)

This reviews how to configure apache.

Most servers are run from the command line, so you may wish to brush up on your bash skills :twisted:

Permissions should not *need* to be changed on your directories.

---

