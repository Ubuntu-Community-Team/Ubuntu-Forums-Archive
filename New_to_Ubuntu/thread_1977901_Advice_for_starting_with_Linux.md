---
title: "Advice for starting with Linux"
date: 2012-05-10
forum: New to Ubuntu
---

### Post by WidmarkRob on 2012-05-10
Hello everybody,

I would like to start using Linux. Like a lot of newbies, who looking for a little advice as to which version would be best to start with.

I've read a few articles and been to a few forums, so far… Ubuntu looks like it would be the easiest to start with.

The question is, "Which Version of Ubuntu"?

I see there is, "Kubuntu, Xubuntu" & there's probably a few more I miss somewhere along the way.

I'm also beginning my software development journey…

Any advice/suggestions would be great…

Thank you in advance

---

### Post by wojox on 2012-05-10
> **WidmarkRob said:**
> The question is, "Which Version of Ubuntu"?
Well that would depend generally on your harware specs.
> I'm also beginning my software development journey&#8230;
Any experience from Windows or Apple?

Welcome to the Forums. ;)

---

### Post by Simian Man on 2012-05-10
> **WidmarkRob said:**
> The question is, "Which Version of Ubuntu"?

I see there is, "Kubuntu, Xubuntu" & there's probably a few more I miss somewhere along the way.
These different versions are only different in what software they come with.  In Linux, important parts of your system - such as the program that draws windows, the program that logs you in, the program that lets you browse files - are interchangeable.  There are different "desktop environments (DE)" that have their own programs for all this.  Ubuntu uses the DE Unity, Kubuntu uses KDE (my favorite), and Xubuntu uses Xfce.

It doesn't matter too much what you start with, becuase you can install all the DEs at once and switch whenever you want.


> **WidmarkRob said:**
> I'm also beginning my software development journey…

What's your experience?  If you've never written any code at all, I'd recommend starting with Python.  It is a very powerful language, and has great support.  It also comes installed with just about every version of Linux.

---

### Post by Bucky Ball on 2012-05-10
Welcome.

What hardware do you have, e.g. RAM and processor? You can try all the *buntus you mention live from the CD so you can try them out before installing. 

Download the ISO of your liking, burn to disk, boot from the disk and when you get to the options screen, 'Try Ubuntu'. 

For low-spec machine try Xubuntu. Ubuntu or Kubuntu should run on a more modern, beefy machine. In the end, it is about what you like and what works for you if you have the grunt to run Ubuntu and Kubuntu (Kubuntu most resource hungry, Xubuntu - and Lubuntu - least). I have a beefy machine but use Xubuntu because it is sleek, simple and fast (I love it and suits the way I work).

The base system of all the *buntus *is the same*, it is the desktop environment and packages that differ, so go for what is most productive. This also means that you can install, say, Ubuntu which uses Unity (or Gnome) desktop environment and then install xfce4, which is the desktop environment only used by Xubuntu, and KDE, used by Kubuntu. Then you choose the desktop environment you want to use at the login screen from 'Sessions'. You can install packages from the other *bunutus into whatever you're using; Ubuntu packages in Xubuntu for instance. You can really start to customise (my desktop is a hybrid Frankenstein would be proud of).

Maybe too much info but just ask for specifics. ;)

@simian man: +1. Beat me to it. ;)

---

### Post by agillator on 2012-05-10
The answers to your questions really depend on your hardware, your experience, and your intended use. I assume you are looking for a general purpose distribution which is why you seem to be looking at Ubuntu. How big a hard drive do you have? How much space can you use for Ubuntu? Assuming you have adequate room and the time and energy, why not try several of them? A basic install of Ubuntu works very nicely in 30GB. That gives you plenty of room to install and to work as long as you are not doing anything initially that eats up disk space. Given that, if you have 300GB available, you can install (heaven help us!) 10 different versions of Ubuntu or whatever, play with them all and see the differences. Then you settle on one, wipe the others, expand the partition of the one you like or reinstall, whatever. Note - this is definitely overkill, but you get the idea.

---

### Post by Bucky Ball on 2012-05-10
> **agillator said:**
>  A basic install of Ubuntu works very nicely in 30GB.

A basic install of Ubuntu works very nicely on 10Gb or less. I've never installed on a partition any bigger than about 12Gb but I use a separate /home partition. 

You don't need to install to try the *buntus. You will get a faster experience from a hard-drive install, though. You will also be able to install third-party and other drivers if you need to. ;)

---

### Post by 3rdalbum on 2012-05-10
Welcome. It can be bewildering to see all the different range of Linux distros, and then decide "I want Ubuntu" and then be faced with this other big choice of "Which Ubuntu".

It's actually rather easy:

**New user**, with a 1 GHz CPU or higher and a gig of RAM or higher? Ubuntu.
**New user** whose computer doesn't fit those specifications? Try Xubuntu or Lubuntu.
**Experienced user who knows what desktop they want?** Install the sub-distro of Ubuntu that has the desktop you want. (Kubuntu, Lubuntu etc)
**64-bit CPU (most are)?** You can use the 64-bit edition if you wish. You'll barely notice any differences, except speed of video encoding may be better on 64-bit.
**Always use the latest stable version (currently 12.04) unless there's a specific reason not to.**

The TL;DR text: Try Ubuntu 12.04, in the 64-bit edition if your computer has a 64-bit CPU; Wikipedia can help if you're not sure about this. If you've already started downloading the 32-bit edition, don't worry - it will work fine on a 64-bit CPU. Also, the filename of the 64-bit disc image has the term "amd64" in it - don't worry, it works on Intel 64-bit CPUs too.

---

### Post by deadflowr on 2012-05-11
30GB is plenty. In terms of which system, I'd say of the four major ubunti(ubuntu,kubuntu,xubuntu,lubuntu)depends first on your system. I put the redline at 1GB ram as a barometer of which to use, generally. If your system runs less than that then lubuntu or xubuntu would be prefered, if more then Kubuntu and ubuntu. Then again you might have 16GB of ram and hate both ubuntu and kubuntu, so it really comes down to taste.

(As an aside, I've had lubuntu running on an old pentiumIII with 256MB ram and it ran fine. Slightly slower but fine.)

As far as developing goes, I don't so I cannot be of help beyond this:
[http://developer.ubuntu.com/]("http://developer.ubuntu.com/")

This should at least help you get a start to learn about developing software and such.

---

### Post by mastablasta on 2012-05-11
> **Bucky Ball said:**
>  
You don't need to install to try the *buntus. 
 
exactly use a USB stick with at least 1 GB and then a programme called Unetbootin or LinuxliveUSB which will help you create a bootable USB stick. if your computer can boto from the USB and if stick is compatible with bios then you can boot it into live session (i.e. instead of install select try it). this loads all system into ram so all changes are lost on restart (unless you created some persistance on the USB stick).
 
either way this is a safe way to try the system, see if the hardware is compatible and see if you like it without making any changes to the core system.
 
i too prefer KDE (Kubuntu) as it's look and feel is similar to windows. My second favourite is Xubuntu, 3rd Lubuntu (very lightweight). I also like the new Unity interface. what is good abotu Gnome (Unity) is that it has a large base of programmes. however most work well in KDE too. KDE also has some awesome applicaitons that are qt based. you might have head of VLC (popular media player), but there are plenty of others as well.
 
All in all all *buntus and their derivatives use same repositories (collection of programmes). 
 
 
there are plenty DE's and windows managers out there beside these big 4 there are also Fluxbox/openbox where most menues are on right mouse click, iceVM (very light widnows manager), E17 (light and prety DE/WM), razorQt (light Qt in development - looks like KDE but uses much less ram), Cinamon (like unity an interface for gnome 3), Gnome Shell (official gnome3), Mate (fork of old gnome)...
 
some distributions that use them:
 
Linux Mint - ubuntu based, but uses Cinamon as DE
Bodhi Linux - ubuntu based but uses E17
 
...
 
not to confuse you further. just try a few in live sesison. the ones you like the most from screenshots. start with Ubuntu and Kubuntu. if you are not happy then Xubuntu (which is very configurable).

---

### Post by sadaruwan12 on 2012-05-11
Welcome to the forums !

For you we cant pin point a distro with out knowing the specs of your computer.

But if you're looking for a all purpose well supported and have one of the greatest forums then go with Ubuntu. Not just the main ditro the other version of it is also good 'cos underneath the engine that drives it is the same.

---

### Post by Ghost_Mazal on 2012-05-11
I haven't seen it mentioned (or I missed it) , but another thing to consider is the lifespan of the Ubuntu you use. IE for how long it will be supported with security updates.

For example , Ubuntu 12.04 is 5 years and Xubuntu 12.04 is only 3 years.
Might also make a difference in what you choose and want.

---

### Post by *^kyfds( on 2012-05-11
> **Ghost_Mazal said:**
> I haven't seen it mentioned (or I missed it) , but another thing to consider is the lifespan of the Ubuntu you use. IE for how long it will be supported with security updates.
 
For example , Ubuntu 12.04 is 5 years and Xubuntu 12.04 is only 3 years.
Might also make a difference in what you choose and want.
 
 
 
are these tips for new users?

---

### Post by Ghost_Mazal on 2012-05-11
> **Thehumorouscheese said:**
> are these tips for new users?

Definitely. Very important information if you are trying to decide what flavour to choose and are not even aware of such things.
I still remember back when I didn't even know that lifespans differ between the flavours and caused me to actually make a wrong choice because of it.

---

### Post by mastablasta on 2012-05-11
> **Ghost_Mazal said:**
> Definitely. Very important information if you are trying to decide what flavour to choose and are not even aware of such things.
I still remember back when I didn't even know that lifespans differ between the flavours and caused me to actually make a wrong choice because of it.

not realyl for someone new. In two years a new Xubuntu LTS version will be out anyway and in 6 months new version that is not lts will come out. to have latest stable version of programmes (and unless you want to mess arround with PPA) you need to upgrade every 6 months....

---

### Post by livewire94 on 2012-05-14
Any of the Ubuntu Distros are fine.  Ubuntu with Unity looks nice, but can be confusing to use.  If your coming from XP, I think Kubuntu, Xubuntu, or Lubuntu would be better.  It also depends on what your hardware specs are. 

I am running Xubuntu and have an AMD Dual Core 3GHZ with 6GB of ram.  I don't like how Unity places your file menus of any program that you are using, on the top panel.  I like to have each window have their own file menus.

---

