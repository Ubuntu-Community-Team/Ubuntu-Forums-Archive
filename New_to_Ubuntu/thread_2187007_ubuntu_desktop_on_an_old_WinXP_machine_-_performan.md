---
title: "ubuntu desktop on an old WinXP machine - performance expectations?"
date: 2013-11-10
forum: New to Ubuntu
---

### Post by alexzendel on 2013-11-10
I'm going to have to send in my Win8 laptop for warranty repair.  This'll take up to two weeks and leave me without a computer - unless I use my old WinXP desktop in the mean time.  The problem: that desktop is agonizingly slow - it takes a minute or two just to launch firefox.  I think some of it is old hardware, but most of it is caused by windows registry breakdown.  So I'm thinking about using Ubuntu desktop and these installation instructions: [http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows](http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows)

This makes it look like the machine can booted into Ubuntu -- and that Ubuntu won't be running on some sort of virtual machine on top of the slow as sin Windows operating system.  Is that a correct assumption?  And if so, should I expect a computer that'll run at a reasonable speed?

---

### Post by Frogs Hair on 2013-11-10
Hello and Welcome

The Wubi / Windows installer is for temporary trial use and creates a root disk  folder inside the windows partition and uses the windows boot loader . If you have no need for XP consider a full  installation of Lubuntu for a low spec machine . I started with Wubi back during the 9.10 release on a Win 7 machine, but never tried  with XP. Prior to that I was running XP Pro which was usable with 256 Mb of memory . If you wrote more about the CPU and Memory we would have a better what might work the best. Lubuntu has 128 Mb memory minimum which is low for a modern operating system.          

[http://www.lubuntu.net/](http://www.lubuntu.net/)

---

### Post by CDR Services on 2013-11-10
For an older machine I would go with 12.04 LTS it's less demanding and more compatible with older hardware. If you have sufficient hard drive space I would install Ubuntu alongside windows! If you boot from the Ubuntu cd and start the install from there the installer will walk you through partitioning ith hard drive. A basic Ubuntu install will run on 10 gig but I recommend at least 20 gig if you have the space the installer will give you the opportunity to import your windows account settings if you have the space available. Even if you don't do that you can still access the windows files from Ubuntu. I would suggest you try running Ubuntu in live mode first to make sure everything works! And cheers!

---

### Post by Mark Phelps on 2013-11-10
> it takes a minute or two just to launch firefox. I think some of it is old hardware, but most of it is caused by windows registry breakdown. 

That's unlikely the cause, since the registry is really a collection of files that operates much like a database.

That's agonizingly slow ... and I wouldn't expect Ubuntu (or even Lubuntu) to run any faster than  that.

Also, I don't think any recent versions will fit on a CD (although, I could be wrong with Lubuntu), and that would require you to boot from a USB stick -- something your old PC most probably will not support.

---

### Post by mörgæs on 2013-11-10
Yes, Lubuntu 13.10 boots from a CD. This one is always a good first attempt when dealing with old hardware.

---

### Post by ckicken-ck on 2013-11-10
...I even installed a 11.something Version on a ASUS eeePC Netbook with an Intel Atom with 1.6 GHz and it ran much faster than XP...
And as a Win7 Starter expanded the RAM usage of a Sony Vaio 13-inch Netbook up to 3/4 of RAM due to the latest updates, I even installed it there parallely. (You cannot even start ans use Firefox proberly!!) There it runs at least twice as fast as Win7.
So try it and it will speed up the old bucket!  :D

---

### Post by sudodus on 2013-11-10
> **Frogs Hair said:**
> Hello and Welcome

The Wubi / Windows installer is for temporary trial use and creates a root disk  folder inside the windows partition and uses the windows boot loader . If you have no need for XP consider a full  installation of Lubuntu for a low spec machine . I started with Wubi back during the 9.10 release on a Win 7 machine, but never tried  with XP. Prior to that I was running XP Pro which was usable with 256 Mb of memory . If you wrote more about the CPU and Memory we would have a better what might work the best. Lubuntu has 128 Mb memory minimum which is low for a modern operating system.          

[http://www.lubuntu.net/](http://www.lubuntu.net/)

+1

Welcome to the Ubuntu Forums *alexzendel* :-)

I would also suggest Lubuntu, but if you post your computer specfications, it will be possible to give more relevant advice.

- Brand name and model
- CPU, RAM (size), graphics card/chip

---

### Post by deadflowr on 2013-11-10
I agree with the suggestion of [Lubuntu]("http://lubuntu.net/").

XP machines run on large array of hardware.
From pentium3's to multi-core systems.

Lubuntu can normally do the same.
Not so much with Ubuntu.

+1 to posting your hardware specs.

---

### Post by Petro Dawg on 2013-11-10
All my computers are old single core XP machines ranging from 1Ghz AMD to 3.8 GHz dual threading Pentium 4s and I've had no problems with Ubuntu 12.04 as long as sufficient RAM is installed.  However, if you have under 1 GIG RAM I would recommend Lubuntu or even Puppy Linux as a good lightweight alternative.

---

### Post by cactus john on 2013-11-10
I'm using 3 old machines a.) P4 w/ 4gb RAM, b.)  Toshiba Satellite Core 2 Duo w/ 4 gb RAM and a HP DC5700 Core 2 Duo w/ 2.5 gb RAM all using 13.10.
The HP is dul booted w/ XP SP2 and screams fast. Toshiba does as well. P4 somewhat slower.
Toshiba and HP are 64 bit

---

### Post by mörgæs on 2013-11-10
Thanks for all the advice, but let's slow down on the posting until original poster returns.

---

