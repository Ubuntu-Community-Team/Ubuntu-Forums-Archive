---
title: "Minimal install help please"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by blk03mitsues on 2008-08-01
i got an old laptop with 64 megs of ram, amd processor.... so i downloaded the xubuntu alternate install cd....
> To install a base system, boot from any Alternate CD and choose "Install a command-line system." It is exactly the same command-line system on Kubuntu/Xubuntu/Ubuntu Alternate CDs. 

i dont see anything that says "install a command-line system" and i dowloaded the "PC (Intel x86) alternate install CD"

since i couldnt find the command line option, i went through the text installation but after 34 minutes stock at 75% installation i decided to shutdown the laptop. figured i ask you people for some help. should i maybe give "Minimal CD Image" a try? i really would appreciate your input....

---

### Post by red_Marvin on 2008-08-01
The server version of ubuntu installs a cli only environment, which you might want to try.

---

### Post by jerome1232 on 2008-08-01
According to [http://www.ubuntu.com/products/whatisubuntu/serveredition/techspecs](http://www.ubuntu.com/products/whatisubuntu/serveredition/techspecs)

> Ubuntu Server Edition 8.04

Ubuntu Server Edition is meant to run on any Intel or AMD x86, AMD_64, EM_64T processors as well as Sun Sparc T1 processors. It requires a minimum of 128Mb of RAM and 1Gb of disk space.

I Couldn't get it to install on a 400 mhz 48 mb ram computer, upgraded it to 102 mb of ram and the install went well. That was 7.10 though.

Not sure if 64mb is enough for the install, I think it will let you leave packages out that won't be needed so they aren't loaded into ram during install (got it to do that once with the 40mbs of ram but I ended up with no network drivers)

---

### Post by Vivaldi Gloria on 2008-08-01
> **blk03mitsues said:**
> i dont see anything that says "install a command-line system" and i dowloaded the "PC (Intel x86) alternate install CD"

Download ubuntu alternate cd and press F4 in the boot menu to choose it. Maybe it also works with the xubuntu alt cd but I haven't tried it.

---

### Post by zvacet on 2008-08-01
@ **blk03mitsues**

With Xubuntu alternate try to install **swap** partition first ( you can put in on the end of HDD ) and then install rest of partitions (root and home).Let your swap be at least double of your ram.

---

### Post by blk03mitsues on 2008-08-01
> **Vivaldi Gloria said:**
> Download ubuntu alternate cd and press F4 in the boot menu to choose it. Maybe it also works with the xubuntu alt cd but I haven't tried it.


i went to research this and thats provably what happened..


[IMG]http://farm4.static.flickr.com/3121/2616055180_56aed7de0f.jpg[/IMG]

when i press F4 with the xubuntu alternate, all i got was "normal"

---

### Post by kerry_s on 2008-08-01
for such low ram DSL is king:
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by Vivaldi Gloria on 2008-08-01
> **blk03mitsues said:**
> i went to research this and thats provably what happened..

when i press F4 with the xubuntu alternate, all i got was "normal"

So everthing is settled then. For cli-only ubuntu install, stay away from k/xubuntu CD but use ubuntu alt CD (or the minimal cd).

---

### Post by blk03mitsues on 2008-08-01
> **kerry_s said:**
> for such low ram DSL is king:
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

but i was unable to confirm that it's in spanish... thats why i was shooting for xubuntu minimal with iceWM...

---

### Post by Vivaldi Gloria on 2008-08-01
> **blk03mitsues said:**
> thats why i was shooting for xubuntu minimal with iceWM...

Also look here:

[http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

---

### Post by rockerphil on 2008-08-01
what you need is the Ubuntu minimal ISO, which can be obtained here:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

just download the one you want, burn it to CD and boot from it. then punch in "cli" to install the base system, hope this helps, 

Phil

---

### Post by Vivaldi Gloria on 2008-08-01
> **rockerphil said:**
> what you need is the Ubuntu minimal ISO, which can be obtained here:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

just download the one you want, burn it to CD and boot from it. then punch in "cli" to install the base system, hope this helps, 

Phil

Actually, the minimal cd installs the same system with the ubuntu alt cd with the F4 option.

---

### Post by blk03mitsues on 2008-08-03
hmmm the install was going smoothly but now it's suck on "localechooser: ex_MX.UTF8..." since half an hour ago

---

### Post by blk03mitsues on 2008-08-03
still stuck, but hardrive has never stopped making noise

---

### Post by blk03mitsues on 2008-08-03
switched to an english install and it also got stuck after "generating locales..."
"en_US.UTF-8..."

it keeps freezing at 75% but i can hear the harddrive doing it's thing. btw i got 8.04 32-bit PC (x86). anybody?

---

### Post by Vivaldi Gloria on 2008-08-03
> **blk03mitsues said:**
> switched to an english install and it also got stuck after "generating locales..."
"en_US.UTF-8..."

it keeps freezing at 75% but i can hear the harddrive doing it's thing. btw i got 8.04 32-bit PC (x86). anybody?

I think your ram is not enough.

---

### Post by angelsguitar on 2008-08-03
Seems that you're running low on system resources to run Ubuntu.

I would suggest you take a look at Puppy Linux.  I have installed it on several low spec machines and always works great.

Another one you can take a look at is TinyMe.

---

### Post by Sef on 2008-08-03
> I think your ram is not enough.

This is the [bare minimal requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements") for Ubuntu:

> Bare Minimum requirements

It should be possible to get Ubuntu running on a system with the following minimum hardware specification, although it is unlikely that the system would run well. You should use the Alternate install CD to attempt such an installation.

    * 300 MHz x86 processor
    * 64 MB of system memory (RAM)
    * At least 4 GB of disk space (for full installation and swap space)
    * VGA graphics card capable of 640x480 resolution
    * CD-ROM drive or network card 

---

### Post by snowpine on 2008-08-03
> **blk03mitsues said:**
> i got an old laptop with 64 megs of ram, amd processor.... so i downloaded the xubuntu alternate install cd....


i dont see anything that says "install a command-line system" and i dowloaded the "PC (Intel x86) alternate install CD"

since i couldnt find the command line option, i went through the text installation but after 34 minutes stock at 75% installation i decided to shutdown the laptop. figured i ask you people for some help. should i maybe give "Minimal CD Image" a try? i really would appreciate your input....

Hi there, unfortunately the Ubuntu installer has a bug that affects computers with 64mb of ram--you can read about it here: [https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/202959](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/202959)

If you are affected, you'll notice the installer stalls at 75% for hours or even days while generating locales...

---

### Post by blk03mitsues on 2008-08-04
well, puppy didnt work for some reason either so i hate to say but i had to go back to XP since it's about the only thing that installs right or that i can actually install.:(

---

