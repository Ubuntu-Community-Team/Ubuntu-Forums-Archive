---
title: "how to install fedora theme"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by copperco2 on 2008-06-26
the theme seems to be good, can anybody give me a real step by step guide on how to..

thanks in advance.

---

### Post by sharks on 2008-06-26
this may help u:

[www.neowin.net/forum/index.php?showtopic=600410](www.neowin.net/forum/index.php?showtopic=600410)
[www.ubuntu-unleashed.com/2007/09/howto-make-ubuntu-look-like-fedora-with.html](www.ubuntu-unleashed.com/2007/09/howto-make-ubuntu-look-like-fedora-with.html)

---

### Post by copperco2 on 2008-06-26
i have tried it but giving me some trouble.
dont understand whats the problem, thats why asking for step by step...installation. i am a novice.. for all practical purposes..and dont want to mess up anything..

---

### Post by copperco2 on 2008-06-26
"sudo dpkg -i gtk-nodoka-engine_O.6-1_i386.deb
dpkg: error processing gtk-nodoka-engine_O.6-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 gtk-nodoka-engine_O.6-1_i386.deb"

this is the error i am getting. pl.help.

---

### Post by slugicide on 2008-07-02
Has anyone figured this out yet?

---

### Post by rossjman1 on 2008-07-02
yes odoka-engine_**O**.6-1_i38
that is supposed to be a zero not the letter 'O'

---

### Post by screaminj3sus on 2008-07-18
I got it working by downloading the source package here: 

[https://fedorahosted.org/releases/n/o/nodoka/gtk-nodoka-engine-0.7.0.tar.gz](https://fedorahosted.org/releases/n/o/nodoka/gtk-nodoka-engine-0.7.0.tar.gz)

make sure you have this package installed:

sudo apt-get install build-essential libgtk2.0-dev

extract that, and in the terminal cd to where you extracted it. If you extracted it to the desktop:

cd /home/USERNAME/Desktop/gtk-nodoka-engine-0.7.0


then just type this:

sudo ./configure --prefix=/usr --enable-animation; make ; make install

bam installed.

If you get access denied like I did try opening a root shell with sudo -i then cd to the directory and install it, that's what i ended up having to do.

---

