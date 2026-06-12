---
title: "Live CD linux."
date: 2008-03-30
forum: Other OS Talk
---

### Post by BluePlum on 2008-03-30
Hey i no theres some Linux that are lightweight and easy 2 run like Puppy, Are there any more? Thx

---

### Post by smoker on 2008-03-30
there are loads, one to try is damn small linux:
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by BluePlum on 2008-03-30
could u run that in ubuntu?

---

### Post by smoker on 2008-03-30
hi, have a look at the website for all the info you require, you can run it as a live-cd, or install it to a hard drive.

you can't run it on top of ubuntu, it is a separate linux operating system,

try it out, best of luck

---

### Post by BluePlum on 2008-03-30
k any other while were on subject? and i thought i could because it says can even be run on windows :P

---

### Post by angry_johnnie on 2008-03-30
There's an "embedded" version of Damn Small Linux which will run inside either Windows or Linux.  It uses Qemu, so it will be slower than a live cd, but it's still worth a try.

The only other way to run Linux, or any other OS, inside your current operating system would be a virtual machine.

[Virtualbox]("http://www.virtualbox.org/") is pretty good.  It also has the advantage of being free and open source.

Virtualbox-ose should be available in Canonical's repository.

---

### Post by BluePlum on 2008-03-30
I wove u :P

Also were 2 DL DAm small linux, I went on site but i clicked download and i clicked on some links and then it got confsing :?

---

### Post by smoker on 2008-03-30
> **BluePlum said:**
> k any other while were on subject? and i thought i could because it says can even be run on windows :P

check their faq:
[http://www.damnsmalllinux.org/wiki/index.php/FAQ](http://www.damnsmalllinux.org/wiki/index.php/FAQ)

it will run as a virtual machine on top of windows. you can install a vm on ubuntu, and run other operating systems through that. look here for info on one:
[http://www.virtualbox.org/](http://www.virtualbox.org/)

there are a variety of other lightweight linux distros here:
[http://bengross.com/smallunix.html](http://bengross.com/smallunix.html)

best of luck

---

### Post by angry_johnnie on 2008-03-30
Here's the link :-)

[ftp://ftp.oss.cc.gatech.edu/pub/linux/distributions/damnsmall/current/](ftp://ftp.oss.cc.gatech.edu/pub/linux/distributions/damnsmall/current/)

You want the one that says dsl-4.2.5-embedded.zip
That's the one that runs inside another OS.

The one that says current.iso is the actual live cd.

---

### Post by BluePlum on 2008-03-30
angry_jhonnie beat u 2 it :P 
THX all

---

### Post by smoker on 2008-03-30
just read this post, seems to be another lightweight distro:
[http://ubuntuforums.org/showthread.php?t=739424](http://ubuntuforums.org/showthread.php?t=739424)

haven't tried it though, but may be of interest,

---

### Post by BluePlum on 2008-03-30
DL dam small linux.zip... How 2 set up in virtual... heh...

---

### Post by angry_johnnie on 2008-03-30
Well, I know for sure the Qemu version runs in windows.  And, according to THEIR frequently asked questions page, it should run within linux, too.  So i went looking for it in my vault, and found it.

It came with a nice README file, which told me how to do it in Windows.  Then, at the very bottom of it, it said something like if you want to run DSL within Linux go to some Qemu website.

So, I did --I was pretty curious at this point-- but ended up just as clueless as I was in the beginning... :lolflag:

So, sorry for making you download that zip file...:confused:  But the FAQ page says it does run in Linux!  (And, maybe, it does.  But they just don't tell you how...)

If you download the current.iso (which is the live cd image) you can --and I'm absolutely sure of this, as I have done it lots of times-- run it as a virtual machine with virtualbox.

Just install virtualbox from synaptic or via apt-get, launch it, create a virtual disk, mount the cd image, boot the virtual machine from it, and that's all there is to it...

Virtualbox is a very good way to test other operating systems.

Sorry again...:oops: I just hope that made sense...

---

### Post by BluePlum on 2008-03-30
now im more confussed... lol

---

### Post by angry_johnnie on 2008-03-31
Alright, here's a very good howto on virtualbox, nstallation and usage.

[http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html](http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html)

---

### Post by BluePlum on 2008-03-31
when i turn it on and click next i get an error :(? some wacky 1 lol

---

### Post by BluePlum on 2008-03-31
Needa no what the erroe code is?

---

### Post by Tim0miT on 2008-03-31
just stick with the ubntu live CD, its the best,all the other ones look realy ugly and some are a fidle to get connected to the internet:lolflag:

---

### Post by BluePlum on 2008-03-31
> **Tim0miT said:**
> just stick with the ubntu live CD, its the best,all the other ones look realy ugly and some are a fidle to get connected to the internet:lolflag:

i need to tun 2 at a time for a reason.

---

### Post by maybeway36 on 2008-03-31
Install the qemu package with apt-get, and you can run DSL from command-line:
```
qemu -cdrom dsl-4.2.5.iso
```
assuming that DSL 4.2.5 is in the current directory.

---

### Post by BluePlum on 2008-03-31
what will that do?

---

