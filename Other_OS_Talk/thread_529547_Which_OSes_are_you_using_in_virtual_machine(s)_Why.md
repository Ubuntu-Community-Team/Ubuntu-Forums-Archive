---
title: "Which OSes are you using in virtual machine(s)? Why?"
date: 2007-08-19
forum: Other OS Talk
---

### Post by tico on 2007-08-19
Just curious about it.

I'm using Windows 2000 in VirtualBox to be able to use my scanner (Canon Lide 500F, not supported in Ubuntu) and because my wife is still addicted to Windows.
I would like also to try some other Linux distros (don't now yet which ones).

---

### Post by wolfen69 on 2007-08-19
ive used xp in virtualbox for my lexmark printer. cant wait to get an HP.

---

### Post by Nekiruhs on 2007-08-19
I use Vista (What?! Shame!) in a VM so I can sync my Zune (GASP! HORROR!). Yeah, I let the iPod hating best-buy clerk talk me into a Zune, before I found linux. Oh well, its beyond return date now.

---

### Post by HotShotDJ on 2007-08-19
I currently use [Windows 2000]("http://www.microsoft.com/windows2000/default.mspx") as a guest OS using [VirtualBox]("http://www.virtualbox.org").  I have three applications that are quite specialized and are not likely to ever have Linux equivalents (unless I pay somebody to develop them for Linux -- also very unlikely!).  I have a few other specialized applets that run under windows, but WINE handles them just fine.

---

### Post by GFree678 on 2007-08-19
XP in VMWare.

Like HotShotDJ I have applications that don't quite work using WINE and don't have Linux equivalents. I also use it to keep a handle on the Windows world.

---

### Post by SOULRiDER on 2007-08-19
I 'use' (rarely actually)  Windows XP because sometime si need a C++ .NET compiler :(

---

### Post by toupeiro on 2007-08-19
RHEL4 as a frontend to the Netapp OS for testing and troubleshooting, Windows XP, Solaris 10 and Nexenta OS

---

### Post by tico on 2007-08-20
to people using XP: how do you handle the "activation" thing, since virtual machine can change easily hardware and makes the activation quite often?

---

### Post by eentonig on 2007-08-20
Two months ago, I 'virtually' booted my XP to do some Photoshop work (Damn that's been too long ago since I did some serious phtography).

For the rest.
- Gutsy off course.
- Trying different linux flavours.
- To do some software installations I want to try before doing them 'live'

---

### Post by toupeiro on 2007-08-20
> **tico said:**
> to people using XP: how do you handle the "activation" thing, since virtual machine can change easily hardware and makes the activation quite often?

Oddly enough, this issue has never occurred for me, even before I virtualized windows.  When I would build a new PC, with an entirely new motherboard, CPU, RAM etc, and reregistered with my same copy of Windows XP, it never complained.

Are you having these problems?  The solution when Microsoft introduced this was to call microsoft and have them de-personalize your product key so you could reregister it.  Maybe there is a way to do this over the net now..

---

### Post by altariel on 2007-08-20
well, I have 
CentOS 4, Debian Sarge 3.1, FC4, FC 7 (soon-to-be-at least), 
Kubuntu 6.10, PCLOS2007 and Mandriva 2007 in **qemu**-images
and 
FC5,FC6 and OpenSuse 10.2 in **VMWare** ... 

***host system***: Kubuntu 6.10 (and FreeBSD 6.2 in the other main partition) 

but then I'm the packager in an open source project :P 
and have found this a GREAT way to build and test the packages (that snapshot feature of qemu is great!)

Edit: and if you like playing around with other images as well and haven't found the OS zoo yet - check out[ http://www.oszoo.org]("http://www.oszoo.org")
tons of simple-and-not-so-simple images to get - even if they aren't as specialized as the VMWare Appliances of course ...

---

### Post by Shazaam on 2007-08-20
I did this...

[http://ubuntuforums.org/showthread.php?t=508061](http://ubuntuforums.org/showthread.php?t=508061)

one afternoon as an experiment. I also have a vm of my physical XP Home installation using VmWare Converter that I re-activated over the web.

---

### Post by Dr. C on 2007-08-20
> **tico said:**
> to people using XP: how do you handle the "activation" thing, since virtual machine can change easily hardware and makes the activation quite often?

I use XP in VMWare and I had to activate only once when I installed it on the VM. It is important ot activate XP after VMWare tools is installed. I have not changed my VM, so I have not had any activation issues. I do not use XP that much anymore so I do not have a need to keep changing my VM all the time.  This is no different from installing XP directly on the hardware. You are allowed some hardware changes before you have to re-activate. I understand it is possible to move your VM to another computer without having to re-activate, just barely, but I have not tried this. If you make to many activations then you have to plead your case with some call center script reader in some far way part of the world. 

By the way Windows Activation, WGA, DRM etc is one of the main reasons I moved to Ubuntu, so the real answer is that I deal with Windows activation by migrating to Ubuntu and phasing out my use of Windows over time.

---

### Post by Tux Aubrey on 2007-08-21
About a year ago I did setup XP to run in VMWare but found I never used it (except to prove a point!) so I deleted it and haven't touched Windows since.

I now use VirtualBox to try out different Linux distros - I currently have virtual installs of Mepis Antix, Zenwalk and dyne:bolic, all of which are very interesting lightweight distros.  I have previously had Mandriva, Fedora 7, PCLinuxOS, Dream Linux, Mepis, Knoppix, Linux Mint, Ubuntu Studio, Ubuntu Ultimate, Gutsy, DSL, Elive and OZ on VMs.  VMs are a great way to try different distros (and even break them!) provided you have the RAM to dedicate.

---

### Post by VorDesigns on 2007-08-21
I run several systems on various VMWare hosts:

One system has an NT4 BDC, a rotating XP install with various applications that don't play nice with anything and an old SuSe Linux distro that I haven't loaded in a while.
I run a development server that has several guest flavors of server applications that I swap out for various client projects.  Sometimes it pays to have the client environment runnable locally when they can't or won't afford a development environment.
When I have some time I'm going to try and convert an old Windows 2000 laptop installation into a VM using their converter but I haven't had the timeor inclination.  I need to keep the laptop OS because of some proprietery VPN clients that won't run on XP or more accurately, I won't install on anything else.

---

### Post by jrusso2 on 2007-08-21
I have played around with a lot of things with the vmware player.  I have tried Nextena, PC-BSD, Open BSD, Solaris, SLED 10, and ReactOS,  just things I normally would not use a whole machine to install just to see if they were interesting enough to dedicate a machine too.

---

### Post by Alterax on 2007-08-21
I use VMWare for virtualization on my Feisty box.  Currently I am doing tests on Gutsy, and have a MS-Windows Server 2003 machine on for training purposes (Since I am on a certification kick here lately, I have it for training purposes until I get my MCSE finished).

It's also good for a couple of other things, too.  I use it to create virtual appliances and then distribute them later to customer sites.

---

### Post by insane_alien on 2007-08-21
XP in vmware so i can run windows apps(little tweak so i get the startbar on my desktop. its pretty cool. [http://www.venturecake.com/10-minutes-to-run-every-windows-app-seamlessly-on-your-ubuntu-desktop/](http://www.venturecake.com/10-minutes-to-run-every-windows-app-seamlessly-on-your-ubuntu-desktop/) i won't deny its a bit flaky at times but 99% of the time it works perfectly.

and a perfect copy of my server (without the massive quantities of data) so i can test modifications before i commit to them for real. works great and i can workout a complete walkthrough so i get it done as quickly as possible.

i also have a machine for testing live distros and there is another for miscellaneous(currently fedora).

---

### Post by -Rick- on 2007-08-21
I have a big 'emu' directory with lot of unix/linux OSs, such as FreeBSD, OpenBSD, Nexenta, for compiling and testing Nixstaller. Further I have Win XP for the very rare moment I need it and an image to play a bit with Syllable.

---

