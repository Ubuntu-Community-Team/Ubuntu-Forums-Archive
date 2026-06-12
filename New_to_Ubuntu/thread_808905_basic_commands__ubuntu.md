---
title: "basic commands  ubuntu"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by jagaprakash on 2008-05-26
give me some basic commands used in ubuntu

---

### Post by xenocide13 on 2008-05-26
well basic commands for what?

---

### Post by Monicker on 2008-05-26
> **jagaprakash said:**
> give me some basic commands used in ubuntu

Something like these?

[https://help.ubuntu.com/8.04/basic-commands/C/]("https://help.ubuntu.com/8.04/basic-commands/C/")

---

### Post by iaculallad on 2008-05-26
> **jagaprakash said:**
> give me some basic commands used in ubuntu

Basic terminal commands on what? For file and directory? For setting attributes? Try googling, there are plenty out there.

---

### Post by Inxsible on 2008-05-26
> **jagaprakash said:**
> give me some basic commands used in ubuntu
There are probably thousands of commands in linux and I don't know anyone who remembers all of them.

What command do you want? What are you trying to do?

If you just want to learn, try googling or going to [www.linuxcommands.org](www.linuxcommands.org)

---

### Post by jagaprakash on 2008-05-27
some of the basics like changing backgroundetc

---

### Post by iaculallad on 2008-05-27
> **jagaprakash said:**
> some of the basics like changing backgroundetc

Background? As in desktop background? Just right-click on your desktop and choose "Change Desktop Background", from there you could select or browse for pictures that could be use as your desktop background.

---

### Post by cdtech on 2008-05-27
To set the background from the command line:

gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/path/to/image.ext"


To set the gnome splash screen from the command line:

gconftool-2 --type string --set /apps/gnome-session/options/splash_image "/path/to/image.ext"

---

