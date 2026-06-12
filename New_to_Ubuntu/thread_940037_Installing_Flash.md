---
title: "Installing Flash"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by Benbow on 2008-10-06
I have downloaded flash player, see below, in my home directory. What do I do to install it?

/home/benbow/flashplayer-installer

---

### Post by bobnutfield on 2008-10-06
Change directory to /home/benbow.  Then, in the terminal, run:

> ./flashplayer-installer

The "dot" and the forward slash in front of the app.

---

### Post by Benbow on 2008-10-06
After starting the installation I got the following. I am a bit confused, does this mean that it is installed or has it failed, which it looks like to me.

----------- Install Action Summary -----------

Adobe Flash Player 9 will be installed in the following directory:

Mozilla installation directory  = /home/benbow/.mozilla

Proceed with the installation? (y/n/q): y
cp: cannot stat `./libflashplayer.so': No such file or directory

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.

chmod: cannot access `/home/benbow/.mozilla/plugins/libflashplayer.so': No such file or directory

Installation complete.

---

### Post by bobnutfield on 2008-10-06
Yes, it should be installed.  To be sure, type in the address bar of Firefo

about:plugins

Shockwave flash should be the first one listed.  That is a colon between about and plugins

---

### Post by SunnyRabbiera on 2008-10-06
typically we install things a bit differently here in linux.
Instead of randomly downloading packages from the net we use repositories and .deb installer packages.
If you need a quick way to install something like flash look no father then this page:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

for other packages you may have to enable third party repositories.

---

### Post by bobnutfield on 2008-10-06
Good point, SunnyRabiera...should have directed the OP thusly.  Just answered his question too quickly.

---

### Post by Benbow on 2008-10-06
Nope, it isn't listed. It failed.

---

### Post by SunnyRabbiera on 2008-10-06
> **Benbow said:**
> Nope, it isn't listed. It failed.

here for now try this:
[http://packages.ubuntu.com/hardy/flashplugin-nonfree](http://packages.ubuntu.com/hardy/flashplugin-nonfree)

download the package for your kernel type and make sure to have firefox shut down when doing it.

---

### Post by Benbow on 2008-10-06
Thanks to both of you, now ok. That's a very good page to know about, Sunny.

---

### Post by SunnyRabbiera on 2008-10-06
your welcome, if you need help on installing packages and the like just ask.
Installing things in ubuntu is just as easy as installing them in windows if you know how.

---

