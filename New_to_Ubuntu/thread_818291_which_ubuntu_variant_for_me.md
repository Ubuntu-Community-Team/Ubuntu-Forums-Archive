---
title: "which ubuntu variant for me????"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by pallav on 2008-06-04
Hi,

First of all Thanks to all Ubuntu developers for making a gr8 operating system.I was a windows Xp user.Now I am switching to Ubuntu but i want to keep my winxp install

Q1>I have an old pc(Pentium 3 1.02 Ghz 512Mb RAm,no separate graphic/sound card)Which ubuntu variant(out of ubuntu/kubuntu) will work faster on my pc.


Q2>**I have formatted my hard drive and have installed Xp on a 8 Gb partition.Now how should i further partition my hard disk(in Ubuntu install window) in order to install ubuntu.

PLease reply fast as I am craving to install this new OS

PAllav AHooja

PS:-While using Ubuntu live CD i have noticed some graphic glitches like when i close a menu or when a tooltip is displayed some part of it is still displayed.Will i face the same problem when i install it on my hard disk

Now

---

### Post by rockerphil on 2008-06-04
ok, in answer to question 1 my best advice would be to use Xubuntu, which uses Xfce as it's interface, super lightweight and simple to use. it can run on as little as (i think) 128 MB of RAM.


in answer to question 2, here's what i'd do, download the Gparted Live CD and allocate about 10 GB for your Ubuntu install with just a blank partition and leave the rest of your hard drive for storage for your 2 OSes, the Ubuntu install CD does the hard stuff for you as far as calculating your systyem's partitions go, so just tell Ubuntu to install to the blank partition you created with Gparted, and when it's done it'll install the GRUB boot loader giving you a nice little list when you boot asking which OS to boot in to. hope this helps

oh, and i doubt that you'll encounter the bugs you had with the Live CD seeing as it's a dedicated hard drive install and will no longer take up as much of your system memory

---

### Post by Promaster91 on 2008-06-04
A1) If you want you can try Xubuntu. It is Ubuntu with the xfce desktop enfiroment. It runs alot faster on old or small pcs and takes up less space. If you don't want to go with that I would just fo with Ubuntu.

A2)It depends. Do you want Ubuntu to take up the whole hard drive? If not, have a separate partition.

PS- No. Don't worry about it.

---

### Post by housam on 2008-06-04
Use the partition editor on the live cd to create 2 new partitions  for ubuntu out of the remaining of your HDD . one for the swap 512 MB and  the other with the rest of the GB for the root ( / ) ext3 format which will have ubuntu.

+1 for ubuntu.

---

### Post by Inxsible on 2008-06-04
1) I tried Xubuntu on a P3-1.1Ghz, 256MB RAM - and it is slow. Therefore I have already moved on to different distros/wms. If you are new to Linux, your best bet would be Xubuntu. and since you have 512 mb ram...it might just be fast enough for you.

---

### Post by FlyingPenguin542 on 2008-06-04
Fluxbuntu is supposed to be quite lightweight. Mind the fact that it's an unofficial Ubuntu distro. It's reportedly a decent choice for older machines, although a little rough around the edges. It's built for lightness and the "flux" is kinda for Fluxbox, a well-known lightweight window manager based on Blackbox. If you'd rather base things off of a more mainstream variant, you could try switching Xubuntu's default window manager with fluxbox and see if the system runs a little faster, as well as taking note of the alternative apps the team chose for lightness.

I've tried Xubuntu, and it's quite easy to use. I'd definitely recommend it for someone who has little Linux experience. And hey, if some of the apps are sluggish, you can always try alternative ones through Synaptic and find others you like better:)

[http://www.xfce.org/about/tour]("http://www.xfce.org/about/tour")

[http://distroblog.com/fluxbuntu-710-rc-review/]("http://distroblog.com/fluxbuntu-710-rc-review/")

And using a GParted livedisk and just blanking out a partition is definitely the way to go. In my experience, you can get some weird errors elsewise. If you wanted, while booted in an xubuntu live disk, you could open a terminal and type in "sudo gparted" (aka Gnome Partition Editor) and blank out a partition that way. Saves you a CD. Then click the install icon, follow the directions, and when it talks about install location, tell it to stick itself in the "largest contiguous free space". The installer will then take care of everything else, like swap space and such.

Before you do ANYTHING though, read the help files and info! Otherwise XP might hang at boot, though since you already HAVE a specific partition for it, you should be fine. Windows takes note of its disk environment and can complain and go psycho if it changes a lot. Solution would be to reset a certain registry value [specific in help files] before cleanly shutting down, and not booting back into windows til AFTER linux is installed. To be on the safe side, take a look at the documentation and confirm before acting. I suppose thats's a good rule-of-thumb for system-invasive stuff.

---

### Post by Duck2006 on 2008-06-04
> **housam said:**
> Use the partition editor on the live cd to create 2 new partitions  for ubuntu out of the remaining of your HDD . one for the swap 512 MB and  the other with the rest of the GB for the root ( / ) ext3 format which will have ubuntu.

+1 for ubuntu.

+1 Ubuntu will run ok on your system. I have on my other system a P3 700Mb 680Mb of ram and it run ok on that system.

---

### Post by D4rkSide on 2008-06-04
well i can share my own expirience with ubuntu (gnome desktop )

i have (i know is pretty old) 

-p3 933 mhz
-6 gig HD
-512mb
-msi nvidia fx 5200 agp

 i tested desktop effects by compiz fusion like burning windows, rotate cube,cube desktop etc... and run like charm im very happy with it

---

### Post by rockerphil on 2008-06-04
DOH, totally forgot about Fluxbuntu, and it was actually my 1st distro. it'll run on as little as 64 MB of RAM, and yea, it's a bit rough around the edges, but ran awesome on my ancient Dell with a 500 MHz processor and 128 MB of SD RAM. so if it can run on that ancient rig i'm sure it'll haul balls on your machine

---

### Post by sayakb on 2008-06-04
As far as distro is concerned, use something lite, yet customizable. You can either use Fluxbox/Openbox or Enlightment (E17). For fluxbox, download [Fluxbuntu]("http://fluxbuntu.org") and for E17, download [OzOs]("http://linux.softpedia.com/progDownload/OzOS-Download-37100.html").

---

### Post by meindian523 on 2008-06-04
Plain old Ubuntu with GNOME would work fine on your machine.I too have 512 MB RAM(processor is dual core) but Ubuntu doesn't have any problem doing it's stuff.:)

---

