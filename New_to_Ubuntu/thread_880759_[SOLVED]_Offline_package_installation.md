---
title: "[SOLVED] Offline package installation"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by spoketire on 2008-08-05
What's the best way to install programs on ubuntu without an internet connection?  I've read about aptoncd, but if I only have a windows computer connected to the internet, that isn't really an option. Is there a way to get just the .deb files and burn them to cd? Would that work?

---

### Post by bobnutfield on 2008-08-05
Yes, you can do that.  Burn them to a CD, transfer them to your desktop, double-click the .deb file, and the package installer will install it for you.

---

### Post by tamoneya on 2008-08-05
to add to what bobnutfield said: go here to get the debs: [http://www.getdeb.net/](http://www.getdeb.net/)

Then burn to CD or usb drive.

---

### Post by spoketire on 2008-08-05
So you can use a usb drive as a software source then? I didn't know that.

My main problem has been finding the .debs, since a lot of sites tell you to just put a url in synaptic instead of just giving you the file. Hopefully getdeb.net will have what I need.

---

### Post by tamoneya on 2008-08-05
unlike the repositories getdeb does not manage dependencies for you.  You may often find that if you transfer a deb over to the ubuntu computer and try to install it it will complain about unmet dependencies. You will then have to go get the deb for the package that was missing.  A little annoying but it should work.

---

### Post by adewale on 2008-08-05
Now this could be very promising [http://wubdepends.sourceforge.net/](http://wubdepends.sourceforge.net/)

---

### Post by spoketire on 2008-08-09
tamoneya, Yes, I was having that problem, and I got so frustrated that I resorted to just hooking my computer up to the internet to install all the dependencies automatically.

adewale, That does look good.  I'll give it a try next time.

---

### Post by safetycopy on 2008-08-09
[This guide]("http://planetoss.com/detail.php?id=13") on PlanetOSS saved my life... It shows you how to get a list of the software you want and its dependencies from Ubuntu and then take that list to Windows or elsewhere to do the actual downloading.

---

### Post by zj3t3mju on 2008-08-10
a command line tool to easy solve it [http://wapt-get.googlecode.com/](http://wapt-get.googlecode.com/)
run very fast write by C

---

### Post by spoketire on 2008-08-20
I tried wapt-get and it worked very well.

Somehow I got a broken dependency and nothing lets me install anything now.  Can I fix this manually without internet if I know what packages are needed?

---

