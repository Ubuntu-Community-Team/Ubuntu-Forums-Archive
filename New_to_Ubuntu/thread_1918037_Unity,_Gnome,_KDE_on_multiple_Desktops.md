---
title: "Unity, Gnome, KDE on multiple Desktops"
date: 2012-01-31
forum: New to Ubuntu
---

### Post by sudo smith on 2012-01-31
I'm new to linux and am currently running Ubuntu 11.10 with unity. I have heard a lot of talk about gnome vs. KDE vs. unity. Is it possible to have unity run in one desktop and gnome or KDE in another, so you can easily switch between them?

---

### Post by raja.genupula on 2012-01-31
> **sudo smith said:**
> I'm new to linux and am currently running Ubuntu 11.10 with unity. I have heard a lot of talk about gnome vs. KDE vs. unity. Is it possible to have unity run in one desktop and gnome or KDE in another, so you can easily switch between them?

yeah of course you do have 

to get Kubuntu desktop
**sudo apt-get install kubuntu-desktop**
to get Xubuntu desktop
**sudo apt-get install xubuntu-desktop**
to get Lubuntu Desktop
[B]sudo apt-get install lubuntu-desktop

[/B]at login screen you can choose what desktop you want . [B]
all the best man . 
[/B]

---

### Post by Paqman on 2012-01-31
No, but you can install all the different desktops, then pick which one you want when you log in.

The main drawback of doing this is that you end up installing all the default apps for each desktop, so you'll end up with several media players/browsers/image viewers/etc. In a menu-based desktop that can get pretty cluttered.

To install a desktop, install the metapackage:
[ubuntu-desktop]("apt:ubuntu-desktop")
[kubuntu-desktop]("apt:kubuntu-desktop")
[xubuntu-desktop]("apt:xubuntu-desktop")
[lubuntu-desktop]("apt:lubuntu-desktop")

---

### Post by mastablasta on 2012-01-31
wouldn't it be better to install a KDE desktop instead of Kubuntu? I mean wouldnt' that reduce the chance of multiple applicaitons? if you installed 4 DE owuld that mean like 4 different power managers running at once when you login?

---

### Post by Bucky Ball on 2012-01-31
> **mastablasta said:**
> wouldn't it be better to install a KDE desktop instead of Kubuntu? I mean wouldnt' that reduce the chance of multiple applicaitons?

 YES! Install KDE and Xfce4 from Software Centre, NOT xubuntu-desktop, etc. You will get tons of unwanted packages and apps if you do that.  Choose the desktop environment you installed from 'Sessions' pop-up menu at login screen.

Don't know that you can do what you suggest unless you run the installs as virtual machines and have them all running at once, for which you will need a ton of RAM and a powerful processor if you are looking at running three or four installs simultaneously.

---

### Post by raja.genupula on 2012-01-31
Hi , yeah i am sorry . 

as compare with my suggestion the above two posts are better .as they mentioned the desktops will installs their default applications and increase your file system weight. so instead of trying mine better to install only desktop environments as they mentioned .

thanks for the post @Bucky Ball ,@mastablasta .

All the best @op.

---

### Post by sanscents on 2012-01-31
> **Bucky Ball said:**
> Install KDE and Xfce4 from Software Centre

What is getting installed in this case?  Things called dependencies?

I didn't know this was possible.  I installed the Edubuntu desktop once after installing Ubuntu, just to see, and never could get my desktop back to normal after, besides having my menus fill with programs.

Aren't their special programs that will be missing?  My Firefox in my Gnome Ubuntu will work just as well if I start with a KDE desktop as Konqueror would?  Is that correct?

---

### Post by QIII on 2012-01-31
If you don't mind using some disk space that you can just reclaim easily, you can download and burn the "spins" of the different 'buntus and install them as virtual machines in VirtualBox.  You could get the "whole experience" of each with its attendant apps and never have to leave the comfort of your primary DE.  

If you decide you don't like something you just delete the virtual machine to reclaim your disk space.  No partitioning required (except virtually in the virtual disk).  The virtual disk is just a "file" like everything else.  Throw it in the trash can if you want. 

If you find you like a DE, just delete the virtual machine and add the DE to your primary.

No worries about cluttering or borking your primary by installing/uninstalling DEs.  You can also test drive other Linux distros.

---

### Post by raja.genupula on 2012-01-31
> **sanscents said:**
> What is getting installed in this case?  Things called dependencies?

I didn't know this was possible.  I installed the Edubuntu desktop once after installing Ubuntu, just to see, and never could get my desktop back to normal after, besides having my menus fill with programs.

Aren't their special programs that will be missing?  My Firefox in my Gnome Ubuntu will work just as well if I start with a KDE desktop as Konqueror would?  Is that correct?

What that message trying to say is , it will install only the core packages which are needed to successfully run a Environment & not the applications those come along with the environment (you gonna have one application for one purpose in each environment eg: ubuntu browser -firefox , Kubuntu -Konquer) . you can run your firefox in kubuntu,ubuntu,lubuntu or xubuntu . 

these Environments are GUI environments to make you interact with Core Ubuntu system . 

in my consideration i will assume them as BODY-Ubuntu core,  dresses - Gnome ,KDE,XFCE,LXDE .insert what ever you want to make it look like that .  so if you go with these no applications of that environment , just a environment. if you want any application regarding that environment you can install it . 

I hope that can help you .

---

### Post by sanscents on 2012-01-31
> **raja.genupula said:**
> I hope that can help you .

Yes, it does.  Thanks!  Like the default Ubuntu install should be called Gubuntu.  If I remove Gnome, I will be in Ubuntu terminal, like the server version.  Is that correct?

Edit - Or Gnubuntu,, or is that sacrilege?

---

### Post by raja.genupula on 2012-02-01
> If I remove Gnome,

Hi man , yes you're i think . but i dont have seen anything like that so i mentioned i think . but you wish to get  pure Gubuntu then i can help you . 

only Gubuntu and its applications , no environment and applications of GNOME . is that you want ?  ?:D

---

### Post by sanscents on 2012-02-01
> **raja.genupula said:**
> but you wish to get  pure Gubuntu then i can help you . 

only Gubuntu and its applications , no environment and applications of GNOME . is that you want ?  ?:D
Well not exactly.  I already have what i think is a pure Gubuntu, which is the 10.04 Ubuntu install i have. But if simply changing to the Xfce4 environment helps lighten my resource load - without giving up my current Ubuntu underlay, or whatever - then I am interested in that.

---

### Post by raja.genupula on 2012-02-01
Then under my knowledge Lubuntu and Xubuntu are the best solutions i can give for you .

EDIT : oh i  mean the LXDE and XFCE environments .

---

### Post by sanscents on 2012-02-01
Well, I wasn't looking for solutions, sudo smith was.  Just sayin' I'm always open to options. Or disabling options, which can be a good thing too lol.  Per.spec.tiv

---

### Post by sudo smith on 2012-07-16
Thanks so much to all posts, sorry I haven't responded earlier. Will mark as Solved. Thanks again. (Love the Ubuntu Community).

---

