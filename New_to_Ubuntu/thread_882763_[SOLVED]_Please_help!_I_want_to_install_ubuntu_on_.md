---
title: "[SOLVED] Please help! I want to install ubuntu on my gateway 450rog laptop"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by mdialogo on 2008-08-07
PLEASE HELP!
PLEASE HELP!
PLEASE HELP!
I am new to Ubuntu Linux and I want to try to install it to my gateway 450ROG laptop.  I boot from the cd. select demo, also the install, the wallpaper appears, but it locks up, the cd drive is reading but still reading nothing happens. Please help I want to learn linux! My laptop has 256 mb ram, is this enough memory for the installation?  I also try to install it inside windows but error appears said cannot access cd some application is using it.  Please help....

---

### Post by overdrank on 2008-08-07
> **mdialogo said:**
> PLEASE HELP!
PLEASE HELP!
PLEASE HELP!
I am new to Ubuntu Linux and I want to try to install it to my gateway 450ROG laptop.  I boot from the cd. select demo, also the install, the wallpaper appears, but it locks up, the cd drive is reading but still reading nothing happens. Please help I want to learn linux! My laptop has 256 mb ram, is this enough memory for the installation?  I also try to install it inside windows but error appears said cannot access cd some application is using it.  Please help....

Hi and welcome, The memory is not enough to support ubuntu live cd. You may choose the alternate cd for install but I believe the system will be to slow. You may look at other distro's like puppy or DSL until you can upgrade your memory.

---

### Post by dje on 2008-08-07
i'd recommend [crunchbang linux]("http://crunchbang.org/projects/linux/") (based on Ubuntu with lightweight openbox window manager), i just put it on a desktop with 256mb ram and it flies along compared to when it had Ubuntu and even Xubuntu.

hope that helps,
dje

---

### Post by billgoldberg on 2008-08-07
> **mdialogo said:**
> PLEASE HELP!
PLEASE HELP!
PLEASE HELP!
I am new to Ubuntu Linux and I want to try to install it to my gateway 450ROG laptop.  I boot from the cd. select demo, also the install, the wallpaper appears, but it locks up, the cd drive is reading but still reading nothing happens. Please help I want to learn linux! My laptop has 256 mb ram, is this enough memory for the installation?  I also try to install it inside windows but error appears said cannot access cd some application is using it.  Please help....

If I were you I would use [fluxbuntu]("http://fluxbuntu.org/").

It isn't as easy to use (at first) but it will run very fast.

--

Partition your hdd using gparted or let (flux)buntu use the entire drive (this will erase windows).

There is a lot of info on this [here]("https://help.ubuntu.com/").

---

### Post by mdialogo on 2008-08-07
how much memory is required with ubuntu 8.04? does it work with gateway laptops? they said that linux can run even with minimal ram. and lastly does dsl also complete like ubuntu? thanks! please reply...

---

### Post by billgoldberg on 2008-08-07
> **mdialogo said:**
> how much memory is required with ubuntu 8.04? does it work with gateway laptops? they said that linux can run even with minimal ram. and lastly does dsl also complete like ubuntu? thanks! please reply...

Sure linux can run on minimal ram. 

You can run fluxbuntu on 64mb ram if you like.

Ubuntu will run on 256mb ram but it will be slow (as I must imagen your windows install is), but you'll need to use the alernate installer (text based).

A Ubuntu based distro like fluxbuntu or crunchbang linux will run a lot faster (actually it will be lightning fast) and should be able to do anything Ubuntu does (no fancy compiz effects though).

-- 

I don't get what you mean with "will dsl also complete with ubuntu".

DSL (damn small linux) is a linux distro for very minimal computers. 

It will be extremely fast on your pc, but a distro like fluxbuntu will be better suited because of it's better package management and bigger repositories.

---

### Post by dje on 2008-08-07
> **mdialogo said:**
> how much memory is required with ubuntu 8.04? does it work with gateway laptops? they said that linux can run even with minimal ram. and lastly does dsl also complete like ubuntu? thanks! please reply...

Ubuntu requires 384 mb ram, it is not designed to be super lightweight as it is a modern distro competing with the likes of vista. the distros posted above (dsl, crunchbang and fluxbuntu) would easily run very well on your machine, check them all out and see which you like :)

dje

---

### Post by snowpine on 2008-08-07
As I mentioned in your other thread, Xubuntu is probably the best choice if you're looking for "like Ubuntu but a bit faster." It is an "official" Ubuntu derivative and has excellent support on these forums. The experience of using Xubuntu is about 90% the same as Ubuntu.

Fluxbuntu and Crunchbang are both awesome and are noticably faster than Xubuntu. Neither of them are "official," so you will need to be more proactive finding support if you run into problems/questions. Crunchbang is more up-to-date than Fluxbuntu and, in my opinion, has a more useful and beginner-friendly "suite" of applications. Fluxbuntu is possibly slightly quicker, though I believe this is largely because of the lightweight applications chosen and because it's based on 7.10 instead of 8.04.

Regular Ubuntu should install on your computer if you use the Alternate CD (not the Live CD, because you don't have enough ram) but it will be the slowest of these options, as it is the "flagship" *buntu product, optimized for more modern computers. Good luck!

---

### Post by mdialogo on 2008-08-07
wow thanks! if ever i successfully install linux on my laptop, will my applications still work? some of my applications are nokia pc suite, cyberlink powerdvd, e-sword, nero? and also an anti-virus, does linux need an anti-virus installed? thanks...

---

### Post by snowpine on 2008-08-07
You have enough RAM that I would recommend trying the Live CDs of Xubuntu, Crunchbang, and DSL (Fluxbuntu does not have a Live CD, unfortunately). This will help you decide which you prefer, without actually installing anything. Remember that the Live CD will be much slower than an actual install, so take that into consideration.

---

### Post by dje on 2008-08-07
> **mdialogo said:**
> wow thanks! if ever i successfully install linux on my laptop, will my applications still work? some of my applications are nokia pc suite, cyberlink powerdvd, e-sword, nero? and also an anti-virus, does linux need an anti-virus installed? thanks...

linux does not need an antivirus and it does not natively run windows applications. you **may** be able to run some in WINE, have a look [here]("http://appdb.winehq.org/") to see if your programs will run. To install wine use the following command in a terminal:
```
sudo apt-get install wine
```

dje

---

### Post by snowpine on 2008-08-07
> **mdialogo said:**
> wow thanks! if ever i successfully install linux on my laptop, will my applications still work? some of my applications are nokia pc suite, cyberlink powerdvd, e-sword, nero? and also an anti-virus, does linux need an anti-virus installed? thanks...

None of your applications will work. Linux is a completely different OS. It is possible to set up a "dual boot" so that Linux and Windows are each installed on separate partitions, that way you can continue to use Windows if you want to use those applications. If you don't set up a dual boot installation, Linux will erase everything on your hard drive and become your full-time operating system.

There is a Linux program called Wine that will allow you to use many Windows applications. However, you shouldn't just assume they will work, you'll need to do some research.

Don't expect Linux to be exactly like Windows, or you will be disappointed! :)

---

### Post by overdrank on 2008-08-07
To the op  mdialogo, please do not create multiple threads on the same issue.
Thanks snowpine
:)

---

### Post by billgoldberg on 2008-08-07
> **mdialogo said:**
> wow thanks! if ever i successfully install linux on my laptop, will my applications still work? some of my applications are nokia pc suite, cyberlink powerdvd, e-sword, nero? and also an anti-virus, does linux need an anti-virus installed? thanks...

[Linux is not Windows.]("http://linux.oneandoneis2.org/LNW.htm")

It will not "play" Windows Applications (the wine project might help you, but don't get your hopes up).

I never use the nokia pc suite and I am not aware if they have a linux installer

Powerdvd: I presume this is a dvd creator. If so, there are lots of alternatives.

E-sword: google tells me this is some bible study software.

If you search in the ubuntu repositories, you'll find some similar applications.

I don't know the quality, being an atheist and all.

Nero: Nero has a linux version, but to be honest I wouldn't buy it.

You'll be wasting your money.

Programs like K3b and Brasero (there are lots of others also) will burn just about everything and there open source and free.

---

### Post by mdialogo on 2008-08-07
is it possible to install linux as a dual boot on my laptop because even if it only have one partition and windows xp is installed in it?

---

### Post by billgoldberg on 2008-08-07
> **mdialogo said:**
> is it possible to install linux as a dual boot on my laptop because even if it only have one partition and windows xp is installed in it?

How big is the partition.

Do you still have room?

If you have 5gb free, you could easily install a linux distro.

Take a look at the gparted live cd (google it) and let it shrink your partition.

Then format the free space as "ext3" or "reiserfs", ... and the the flux(buntu) cd will do the rest for you.

---

### Post by snowpine on 2008-08-07
> **mdialogo said:**
> is it possible to install linux as a dual boot on my laptop because even if it only have one partition and windows xp is installed in it?

Absolutely it is possible. The installer should give you an option that says "resize existing partition and use freed space." It will create the necessary partitions for you. There is also an excellent guide to partitions here: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

You definitely want to back up any data first. Just in case!

Also, the Live CD gives you a good way to experiment with Linux before making any permanent changes/installing anything.

---

### Post by Sef on 2008-08-07
> is it possible to install linux as a dual boot on my laptop because even if it only have one partition and windows xp is installed in it?

Read [Psychocats]("http://psychocats.net/ubuntu").

For installing with the alternate cd:  [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/").

---

### Post by ooobuntooo on 2008-08-07
> **mdialogo said:**
> is it possible to install linux as a dual boot on my laptop because even if it only have one partition and windows xp is installed in it?

Try Wubi!

[http://wubi-installer.org/](http://wubi-installer.org/)

The easy way to install Ubuntu, Kubuntu or Xubuntu on the same hard disk as Windows. No partitioning required.

---

