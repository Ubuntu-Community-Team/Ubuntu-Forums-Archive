---
title: "Can not install Crossfire! Please Help!"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by Akumos on 2008-10-29
Hi, I've been trying for days no to install Crossfire on Ubuntu. I followed information from the internet on earlier problems but now I'm stuck.

I'm using Kconfigure to install it. It configures but I get these warnings:

configure: WARNING: X11 not found - will not build X client
checking for GTK2... configure: WARNING: GTK 1 not found - not building building gtk-v1 client
configure: WARNING: GTK+ 2 libraries not found - will not build gtk-v2 client
config.status: WARNING:  Makefile.in seems to ignore the --datarootdir setting
config.status: WARNING:  gtk/Makefile.in seems to ignore the --datarootdir setting
config.status: WARNING:  x11/Makefile.in seems to ignore the --datarootdir setting
config.status: WARNING:  common/Makefile.in seems to ignore the --datarootdir setting
config.status: WARNING:  sound-src/Makefile.in seems to ignore the --datarootdir setting
config.status: WARNING:  gtk-v2/Makefile.in seems to ignore the --datarootdir setting
config.status: WARNING:  pixmaps/Makefile.in seems to ignore the --datarootdir setting
config.status: WARNING:  gtk-v2/src/Makefile.in seems to ignore the --datarootdir setting
config.status: WARNING:  help/Makefile.in seems to ignore the --datarootdir setting
config.status: WARNING:  utils/Makefile.in seems to ignore the --datarootdir setting

Then I get no errors when I click 'Make' and the following errors when I click install:

/usr/bin/install: cannot create regular file `/usr/local/bin/cfsndserv': Permission denied
make[2]: *** [install-binPROGRAMS] Error 1
make[1]: *** [install-am] Error 2
make: *** [install-recursive] Error 1


Any help is greatly appreciated. Thanks.

---

### Post by dracayr on 2008-10-29
I guess you want to install the client? simply enter:```
sudo apt-get install crossfire-client-gtk2
```

EDIT: for sound and images, also install crossfire-client and crossfire-client images in the same manner. The overall command is:

```
sudo apt-get install crossfire-client-gtk2 crossfire-client-images crossfire-client
```
dracayr

---

### Post by Akumos on 2008-10-29
That easy? Might sound stupid but how do I run it after I did that?

Thanks BTW

---

### Post by Perfect Storm on 2008-10-29
Easist way do what dracayr say. But if you insist compiling it;

You need this;
```
sudo apt-get install libx11-dev libgtk2.0-dev
```

---

### Post by Perfect Storm on 2008-10-29
> **Akumos said:**
> That easy? Might sound stupid but how do I run it after I did that?



```
gcfclient2
```

You can make a launcher by in the panel tab also.

---

### Post by Akumos on 2008-10-29
Thanks, it's loaded fine. Where is this installed on my PC. Is there a folder an directory it's in. Can I get an icon shortcut for it?

Thanks

---

### Post by Perfect Storm on 2008-10-29
```
alacarte
```

Make a "New Item" in Games;

Name: Crossfire GTK2 Client
Command; gcfclient2
Comment: Whatever you prefer.


There's no icon for crossfire, but you can find or make one that would fit.

---

### Post by NTpspE on 2011-08-02
Hey, this is a majorly old topic and i'm sorry for gravedigging. 
I'm running ubuntu 11.04 now, and i've installed crossfire-client, crossfire-client-images and crossfire-client-gtk2 and no matter what command i use "cfclient gcfclient gcfclient2" none of them are recognised :/

---

### Post by Fury6203 on 2011-08-25
I need help with this to, I'm new around here and only been a couple of days on ubuntu CrossFire is my favorite Windows game I did everything you said up there but I'm and I have no idea what to do with the gcfclient2 code. I would greatly appreciate any help.

---

### Post by overdrank on 2011-08-25
Hi and please start a new thread for your issue. Thread closed :)

---

