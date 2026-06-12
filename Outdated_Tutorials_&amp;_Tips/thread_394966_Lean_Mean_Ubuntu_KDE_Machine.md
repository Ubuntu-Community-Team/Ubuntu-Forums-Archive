---
title: "Lean Mean Ubuntu KDE Machine"
date: 2007-03-27
forum: Outdated Tutorials &amp; Tips
---

### Post by ranjandatta on 2007-03-27
**Background: **
Kubuntu has never worked for me, It is slow and sluggish, maybe also neglected compared to Ubuntu and Xubuntu. Non apt based KDE Ditros  are a pain, Mepis makes too many modifications including the kernel and is difficult to maintain using apt/synaptic. The only solution seems customize your own KDE machine.

**Who should try this:**
I am no Linux expert. Infact this is my first post on these forums. I have used Linux only for a year as my primary OS. I am not comfortable yet with CLI. If I can do it anyone can!

**Credit where its due**
Sunrat on Debian forums wrote [this]("http://forums.debian.net/viewtopic.php?t=10876") post, which gave me the courage to try this out

Enough blah blah....

1. [Download]("http://ftp.leg.uct.ac.za/pub/linux/ubuntu-releases/feisty/") the server install CD for your machine, burn it, install it. Since I am a web developer, the server install gives me a local web development environment. If you do not need the server you may not install the packages. The install gives you an installation without X or any DE.

2. On logging in in your CLI enviorment, first update your mysql root password if you have installed servers

```
mysqladmin -u root password NEWPASSWORD
```

3. Perform Upgrade

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

4. Install X

```

sudo apt-get install xorg xorg-dev

```

5. Install KDE and other essentials

```

sudo apt-get install kde-core alsa-base alsa-utils synaptic kdm build-essential

```

6. Reboot, Your machine will present you with KDM for GUI login. Login

7. Install Apps & Utilities

```

sudo apt-get install kdeaddons-kfile-plugins kdegraphics ttf-bitstream-vera konq-plugins kdemultimedia-kappfinder-data kdemultimedia-kio-plugins kdemultimedia-kfile-plugins kicker-applets ark bzip2 p7zip-full unzip unrar mozilla-thunderbird firefox gimp inkscape gqview imagemagick quanta kompare cervisia kword kedit keep kdf kdict kget knemo krename ksysv ktux kuser

```

8. Install mutimedia support and apps

```

wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
sudo wget http://medibuntu.sos-sts.com/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update
sudo apt-get install k3b cdrdao dvd+rw-tools kaffeine kaffeine-mozilla amarok w32codecs flac libdvdcss2 ffmpeg mozplugger easytag kaudiocreator kmix

```

9. Install Headers

```

sudo apt-get install linux-headers-$(uname -r)

```

10. Install your Graphics Card Drivers

For Nvidia: Download the latest driver into your home folder, Close X and Install

```

sudo sh NVIDIA-Linux-x86-1.0-8776-pkg1.run

```

For Other Cards: You are on your own

11. Install Java

```

sudo apt-get install sun-java5-jre sun-java5-plugin

```

12. Install Goodies

```

sudo apt-get install kwin-style-crystal kscreensaver-xsavers xscreensaver xscreensaver-gl

```

13. More Goodies
Add deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) dapper 3v1n0 to your /etc/apt/sources.list
```

wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install libdivxdecore0 libdivxencore0 flashplugin-nonfree gtk2-engines-gtk-qt qtcurve qtcurve-gtk2

```

14. All thats left is to install mp3 support. The quickest way in Feisty is to open an mp3 file using Amarok.

The installation is complete. Its lean and faster than Ubuntu and its KDE!!

---

### Post by nrwilk on 2007-04-09
Thank you.  I was looking for something just like this.

I will let you know how it works for me.

I'm tired of all the extra crap that kubuntu-desktop includes that I never use.  I'd rather install stuff as I need it.  After all, it's only a repository away...

:)

---

### Post by ranjandatta on 2007-04-12
How did it go?

---

### Post by nrwilk on 2007-04-12
> **ranjandatta said:**
> How did it go?

Well, My desktop is running Dapper, and my Laptop runs Edgy.  So, I'm waiting for a final Feisty release to use your tips.  I'll be installing it on both machines.

I will definitely let you know how it goes when Feisty is released.  I will probably do the installs that weekend.

Thanks again! :D

---

### Post by odelay on 2007-04-13
I'm a relatively new Kubuntu user.

So far I like it a lot better than Ubuntu--mostly because I like the standard apps more.  It has more of an OS X iLife-type feel to it, IMHO.  I personally haven't noticed any real speed differences between the two.  Perhaps it's b/c my computer is only a year old.

As I said...I'm pretty new at this, so I was wondering how does this make k/ubuntu "faster" instead of just "smaller."  How would this be different than installing Kubuntu than just removing the applications and associated files you don't want?  Would doing that make things faster, or just free up HD space?

Thanks...I haven't tried the guide, but it looks very well written.  Good job.

---

### Post by pelikan on 2007-04-13
Yes it makes it faster.

Thanks for this guide. :) I've been playing with server installs. I ended up prefering to use kde-core on top. Your guide helped me out quite a bit. I picked out what I needed on my system and just installed that.

Now I'm thinking of removing kdm and using something smaller to auto-login.

---

### Post by pelikan on 2007-04-19
Here's my Feisty install. It gives me the basics, on top of which I can install any other programs I need. I use kdebase instead of kde-core because it's smaller and I don't need everything in kde-core. I like Feisty's video card driver and multimedia installs from Add Remove Programs and Restricted Manager. This gets my video card and every kind of streaming video working easily. 

1. Command line install from alternate install CD.

2. Get X and KDE

sudo apt-get update

sudo apt-get install xorg 

sudo apt-get install kdebase kdm

3. Type startx to get into KDE and then install video card driver

sudo apt-get install restricted-manager

sudo restricted-manager (runs it so you can install your video card drivers, ATI or Nvidia).

4. Reboot and Install Multimedia Support

sudo apt-get install firefox (I get the fasterfox extension too)

sudo apt-get install gnome-app-install (this is Add Remove Programs)

Install Ubuntu Restricted Extras with Add Remove Programs ([guide]("https://help.ubuntu.com/community/RestrictedFormats")) (this is java, flash, etc.)

Follow [Medibuntu guide]("https://help.ubuntu.com/community/Medibuntu") for DVD and W32 codecs.

sudo apt-get install mplayer

Install MPlayer plugin for Mozilla with Add Remove Programs

5. Get email program

sudo apt-get install mozilla-thunderbird

Done.

---

### Post by nrwilk on 2007-04-20
heya guys, I've got mine working pretty well, but I want to get the default kubuntu KDM and splash artwork installed.  I found a package which I think has these things, but I cannot install it now as I am at school on my laptop, and my new feisty setup is on my desktop at home.  Feisty goes on the lappy tonight.

Can anyone please verify for me that this is the package which contains the artwork I am searching for?  Also, if this is the correct package, what else does it install?  What are the "settings" to which it refers?

```
kubuntu-default-settings          - Default settings and artwork for the Kubuntu desktop
```

Thank you! :)


**[COLOR="Red"]EDIT:[/COLOR]**
I found the list of files which this package contains.  It seems that it IS the package which I am seeking.
list of files [here]("http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=kubuntu-default-settings&version=feisty&arch=all").

---

### Post by brlmedia on 2007-04-22
great post, just tried it and it was successful, thanks

---

### Post by sad_iq on 2007-06-15
Ok...works great here...just a small question...how do i set up the network (gateway, route, dns...etc.) ...i had something on my standard kubuntu install...but I'm unable to find anything now!!!

And just a tip...kubuntu.org explains how to  use adept for importing signature files...maybe newbies will find it easyer instead of using the konsole(I can't find any such function with synaptic)!!!

---

