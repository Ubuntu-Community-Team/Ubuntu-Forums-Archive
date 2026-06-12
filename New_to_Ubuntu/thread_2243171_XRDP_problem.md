---
title: "XRDP problem"
date: 2014-09-06
forum: New to Ubuntu
---

### Post by PWMKzzJ on 2014-09-06
I have several Ubuntu virtual machines running on my server and for some reason xrdp will stop working at random. It will be fine one minute and then sometimes when I connect with krdc it will just display a blank screen. I read the articles that instructed you on how to edit the config files and manually specify a session like Unity or KDE. I did that right after building the VM and it worked for a while. Now what I am having to do is remove and re-install it if this happens. I'm using "sudo apt-get remove --purge xrdp" and from what I understand that should also remove the config files? I'm hoping that someone can help me find a fix other than removing and re-installing it every time.  Also after doing that I am getting am error immediately after I log in that says "KDE daemon closed unexpectedly" however everything works perfectly.

---

### Post by PWMKzzJ on 2014-09-06
Im not sure if it is related but I just ran updates through SSH and then logged back in through krdc and it said that X11 couldn't write to the /tmp folder and will exit. Disconnected and tried again and now there is no error message and just the blank display.

---

### Post by gordintoronto on 2014-09-07
Have you tried x11vnc?

---

