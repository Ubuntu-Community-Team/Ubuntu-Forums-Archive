---
title: "beta fails to update"
date: 2011-09-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lime4x4 on 2011-09-02
Installed a fresh copy of the beta 64 bit. After installing i run update manager and it installed more packages. Now when i run update manager it complains about it can't calculate the amount of space required. If i try to update thru a terminal it shows a big list of packages that have been kept back. Anyone else running into this?

---

### Post by cariboo on 2011-09-02
Don't use update-manager to update a testing release, use either the terminal, or synaptic.

---

### Post by jerrylamos on 2011-09-02
> **cariboo907 said:**
> Don't use update-manager to update a testing release, use either the terminal, or synaptic.

sudo synaptic
<enter password>
sudo: synaptic: command not found

What do the developers think the users/testers are supposed to do?  I sure hope the developers ship the Beta 1 with an update capability ready to use.

I happen to do 
sudo apt-get install aptitude
but I get the distinct impresseion Ubuntu developers don't like aptitude.

I use it by creating an exec. 
gedit <any name you want>

#! /bin/bash
sudo aptitude update
sudo aptitude safe-upgrade

save 
sudo chmod 777 <any name...>

to run it 
./<any name ....>

if you like it, then
sudo cp <any name ....> /usr/bin

then to run it you don't need the ./

Jerry

p.s.  I've had apt-get update, apt-get dist-upgrade destroy installs several times.

---

### Post by coffeecat on 2011-09-02
> **jerrylamos said:**
> What do the developers think the users/testers are supposed to do? 

```
sudo apt-get install synaptic
```

:wink:

Have you forgotten this already, Jerry? (You posted in it.)

[http://ubuntuforums.org/showthread.php?t=1831283](http://ubuntuforums.org/showthread.php?t=1831283)

And...

> **jerrylamos said:**
> sudo synaptic
<enter password>
sudo: synaptic: command not found

Tch, tch! Using sudo with a graphical app! Not in front of the children. :o  

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by cariboo on 2011-09-02
If you have synaptic installed, just click the dash icon, and type **syn** then click the icon, a dialogue box automagically pops up for you to enter your password.

If you click the second from the left icon on the very bottom of the dash, it will bring up the most used programs.

See the screenshot.

---

