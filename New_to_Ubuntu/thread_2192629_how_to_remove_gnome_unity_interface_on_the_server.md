---
title: "how to remove gnome unity interface on the server?"
date: 2013-12-08
forum: New to Ubuntu
---

### Post by 007casper on 2013-12-08
I am using 10.04 on a server.  I want to remove the gnome unity interface from the server.  What is the best way to uninstall it?

---

### Post by 007casper on 2013-12-08
is it 
> 
sudo apt-get remove ubuntu-desktop

can someone confirm that?  It is on a live production server

---

### Post by deadflowr on 2013-12-08
How did you install the gnome unity interface to begin with?

---

### Post by 007casper on 2013-12-09
I set it up as a server first, and then install ubuntu-desktop.  I would like to get rid of the desktop interface now.  I dont need it.

I installed it by... 
> sudo apt-get install ubuntu-desktop

cause of that I figured using... 

> sudo apt-get remove ubuntu-desktop 

is that correct way to remove the desktop unity interface?... does it make sense?  I wanted to check with the community before I hit 'enter'... since it is on a live production server.

---

### Post by deadflowr on 2013-12-09
I believe when you hit enter it should list things that will be removed, if anything beyond the ubuntu-desktop metapackage.

Curious though, was unity actually the desktop?

---

### Post by 007casper on 2013-12-09
unity was the actuall desktop

---

### Post by deadflowr on 2013-12-09
> **007casper said:**
> unity was the actuall desktop

But unity isn't(wasn't, as lucid desktop is dead;end of life) part of the the ubuntu-desktop package for lucid.
Gnome2 desktop was.
So did you install unity or the ubuntu-desktop?

---

### Post by 007casper on 2013-12-09
> sudo aptitude remove ubuntu-desktop

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  firefox-3.0{u} firefox-3.5{u} ubufox{u} 
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 336kB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 291017 files and directories currently installed.)
Removing firefox-3.0 ...
Removing firefox-3.5 ...
Removing ubufox ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

It doesnt remove the desktop and all the UI stuff that comes with it... 

?

---

### Post by monkeybrain20122 on 2013-12-09
Unity-desktop is just a meta package, removing it has no effect. How did you get unity in 10.04 in the first place???!!

If you remove compiz that would be a sure fire way because unity is a compiz plugin but that will certainly leave you with a broken system.

---

### Post by deadflowr on 2013-12-09
Here is the list of all the packages that the ubuntu-desktop mate-package installs on lucid
[http://packages.ubuntu.com/lucid/ubuntu-desktop](http://packages.ubuntu.com/lucid/ubuntu-desktop)

All the depends are automatically part of it and the normally so are the recommends(unless you opt out of them).
The suggests are usually part of separate packaging.

If you installed unity
then use the apt-get remove option with unity, and see if that removes it.

On other notes, if you don't want or have to have an X session on the server/ meaning you don't need a gui, then you will probably need to remove the xserver-xorg packages as well.

---

### Post by 007casper on 2013-12-09
> sudo apt-get install ubuntu-desktop 

thats how I installed desktop

deadflowr thanks for the list.

---

### Post by philinux on 2013-12-09
On the server what does this show just to be certain.

```
lsb_release -a
```

---

### Post by 007casper on 2014-02-05
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.4 LTS
Release:	10.04
Codename:	lucid

it is not unity... it is Gnome2

---

