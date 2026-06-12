---
title: "installing server edition"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by rabatitat on 2008-08-12
For those making the switch:

1. DO NOT USE Ubuntu Server Edition AS A BASE FOR BUILDING A DEVELOPMENT MACHINE.

My goal WAS to make a light LAMP stack with a Gnome WM for developing web apps... I spent more than 24 hours setting up the server install... RAID??? (Don't even bother if it's not hardware RAID... Setting up FakeRAID ain't worth it...)

Used Aptitude to install bind, apache, php, mysql...

setup up those things for my uses with no sweat...

The GUI:

aptitude installed gnome-core, gdm, xorg... Ran into a few snags with the applets... Fixed them all... Started tweaking and adding tools... Did it all successfully...

FTW!!!

I can sleep!!! Installed Update Manager before I went to sleep... Ran update without even thinking and checking...

BOOM!

I wake up to find Update Manager installed the whole Ubuntu desktop edition... OUCH...

---

### Post by overdrank on 2008-08-12
Moved to ABT

---

### Post by hyper_ch on 2008-08-12
> **rabatitat said:**
> 1. DO NOT USE Ubuntu Server Edition AS A BASE FOR BUILDING A DEVELOPMENT MACHINE.
Why not?

> **rabatitat said:**
> My goal WAS to make a light LAMP stack with a Gnome WM for developing web apps...
why installing a gui on a server which you want to use for developping web apps?

> **rabatitat said:**
> Used Aptitude to install bind, apache, php, mysql...
You want a server to be light-weight hence you should rather use apt-get as aptitude also installs teh recommended packages.

---

### Post by Joeb454 on 2008-08-12
If you want to run a server, personally I think it's worth getting used to the command line. My server is a CLI only system, it runs a LAMP server, with a Samba share for the entire network, and an ssh server (no ssh'd users can see the contents of the samba share either ;))

It was all really easy to set up, just a little CLI knowledge required (there's plenty of guides)

---

### Post by jonabyte on 2008-08-12
> **rabatitat said:**
> For those making the switch:

1. DO NOT USE Ubuntu Server Edition AS A BASE FOR BUILDING A DEVELOPMENT MACHINE.


I am using this as a web development box and it works very well. In fact, it only has 64mb of ram...mind you I do need to kick it every so often.

---

### Post by Cypher on 2008-08-12
It sounds like you'd been better of starting with the Desktop addition and installing the LAMP stack on it..

If you want to use the Server addition, then you should be comfortable leaving it at a console and not necessary use that for Web development as well..

---

### Post by rabatitat on 2008-08-18
Yup I did do a Desktop install with a LAMP stack added.

Anyway I was pressed for time so I scrapped the server and reverted to desktop with LAMP.

The project's for an intranet that uses a LAMP server. This made me look into Linux and Ubuntu convinced me to switch.

I have no problems with using a command line if it's for server only but with the project I'm doing I do need a GUI. I don't have a spare to set up as a server (I do, but my wife would kill me...)

I know that it's doable I just didn't have the time yet... My Linux experience is mostly up to the level that I can configure and run what's already installed and I haven't done a Linux install outside of the basic setup options and installation of packages only.

I will however learn building/compiling my own Linux since I've found the fun of computing again with Linux (Windows is a shroud and a black hole...)

Also, I have my problems with the default install of Ubuntu Desktop as the content development tools lock up on me (Gimp, Inkscape, etc.). This problem I didn't have with Adobe on Windows even with background load (Media player, uTorrent, and even rendering video). So, I will address this when I finish my current project to enrich my Linux life. :D So far the problem lies with any of the following:

1. My n00bness.
2. ALSA - Sketchy support for my soundcard (Audigy Value).
3. The 2.6-generic kernel I hear isn't optimized for media.

Hopefully it isn't number 2 since I hate throwing hardware at a problem.

---

