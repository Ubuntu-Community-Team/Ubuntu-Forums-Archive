---
title: "new to ubuntu forum intro"
date: 2012-12-07
forum: New to Ubuntu
---

### Post by nasweitzer on 2012-12-07
Hi I'm new to ubuntu forums my dad sent me here for information. I'm 9 years old and my dad and I are going to work together on building an ubuntu distro os from scratch using LFS so any help or advice on building ubuntu from source would be appreciated.  Should I install all packages or build each package from source

---

### Post by nasweitzer on 2012-12-07
> **nasweitzer said:**
> Hi I'm new to ubuntu forums my dad sent me here for information. I'm 9 years old and my dad and I are going to work together on building an ubuntu distro os from scratch using LFS so any help or advice on building ubuntu from source would be appreciated.  Should I install all packages or build each package from source
  should I use LFS or ubuntu image source
note i'm new

---

### Post by sandyd on 2012-12-07
If you are talking about Linux From Scratch, Ubuntu and Linux From Scratch are two different things.

Ubuntu is a binary distro, which means the package manager installs binary packages.

Linux From Scratch is a different Linux distribution that installs  all programs from source code.

---

### Post by nasweitzer on 2012-12-07
hows the best why to go about it want to build ubuntu from scratch including the image file from source this is a learning thing for me and my dad

---

### Post by Ji Ruo on 2012-12-07
You probably won't find instructions on building Ubuntu from source code. Most people use Ubuntu to avoid having to do stuff like that. It is definitely possible, but if you are really set on doing this you might have to adapt the Linux From Scratch (LFS) instructions. I think you would be better off following the LFS guides with a standard linux kernel, as this will be hard enough. You will have more guidance and more people to turn to if you run into trouble. If you get it working, it will definitely be an achievement and you can use your new knowledge and skills to try doing it with Ubuntu after that. You can try asking on the LFS mailing list too: [http://www.linuxfromscratch.org/mail.html](http://www.linuxfromscratch.org/mail.html) - they might be able to give you some good advice.

---

### Post by nasweitzer on 2012-12-07
we printed the book fore LFS

---

### Post by nasweitzer on 2012-12-07
should I us ubuntu 12.04 minimal to build and how would i make a live cd from it

---

### Post by amsweitzer on 2012-12-07
I'm letting him research the project we downloaded the book LFS 7.1 on ubuntu 12.04 we were looking into building from scratch I have a clean install of 12.04 alternate install on a disk that Nathan will use as his working partician and the project will encompass building either from source or from minimal disk I prefer source for him to do the project so he can get a full understanding of the build process and structure  of Ubuntu and get a confidence in using terminal its really just a basic os using gnome shell as gui no unity no cairo as he like me doesn't like unity I have an install of 12.10 with unity gnome-shell and kde on it and let him look at the various desktops and choose his desktop he prefers gnome classic using shell have already gone into synaptic package manager and wrote a download script for all game packages within repos maybe his thread should be moved to programming and development.

---

### Post by zombifier25 on 2012-12-08
LFS and Ubuntu Minimal are different from each other. Ubuntu Minimal is the base Ubuntu system and nothing more. From it you can install the packages you need (X, a display manager, etc)

LFS allows you to build a new Linux system from scratch, from the ground up. Building a LFS system takes a lot of time, and it's generally for educational purposes only.

It's not exactly clear on what you guys want, so you should elaborate.

---

### Post by Paqman on 2012-12-08
> **nasweitzer said:**
> should I us ubuntu 12.04 minimal to build and how would i make a live cd from it

That would be a better place to start than LFS. LFS is a very long, very technical, very laborious way to build Linux. It's apparently an excellent education in the nuts and bolts, but not suitable for someone new to Linux. Put that one down for later.

Starting with the minimal image will give you a command line system, then you can add packages. It'll teach you about the package manager and how the dependencies build up a complete system. That's an important part of Linux, as it's essentially a modular system.

Once you've got a system built you can use [Remastersys]("http://www.geekconnection.org/remastersys/") to create a Live CD of it.

---

### Post by cbennett926 on 2012-12-08
I honestly think you two would enjoy building an Arch Linux together, it's much more fulfilling and not *_too _*difficult!

---

### Post by nasweitzer on 2012-12-08
Its  educational purposes to learn the basis of how Ubuntu works its structoral basis and get a understanding of using programming in linux by building the code from scratch

---

### Post by cbennett926 on 2012-12-08
> **nasweitzer said:**
> Its  educational purposes to learn the basis of how Ubuntu works its structoral basis and get a understanding of using programming in linux by building the code from scratch


Then maybe try and get an older release of Ubuntu, things get kinda weird after 11.04, it's easier to work with gnome 2

---

### Post by nasweitzer on 2012-12-08
my dad said to use minimal

---

### Post by DuckHook on 2012-12-08
> **nasweitzer said:**
> Its  educational purposes to learn the basis of how Ubuntu works its structoral basis and get a understanding of using programming in linux by building the code from scratch

Your sentiments are laudable, but what you are trying to do is akin to setting out to build a spaceship from scratch. Would suggest that you start with a more attainable goal first. Then go from there. I would second the recommendation to start with minimal install, learn package structure, file structure, dependencies, command line tools, etc before launching for the stars.

---

### Post by lisati on 2012-12-08
> **nasweitzer said:**
> my dad said to use minimal

Is it possible that all your Dad meant was to install just enough to do what you need to do with the system? It's possible to do that without mucking around with compiling from source.

---

### Post by nasweitzer on 2012-12-08
> **cbennett926 said:**
> Then maybe try and get an older release of Ubuntu, things get kinda weird after 11.04, it's easier to work with gnome 2
thanks

---

### Post by Paqman on 2012-12-09
> **cbennett926 said:**
> Then maybe try and get an older release of Ubuntu, things get kinda weird after 11.04, it's easier to work with gnome 2

A minimal install is the same no matter which version, I would say use either the latest version (12.10) or the latest LTS (12.04). If you're installing from a minimal base then you have the choice of multiple DEs, I would suggest experimenting with several, as it shows off the modularity concept.

---

