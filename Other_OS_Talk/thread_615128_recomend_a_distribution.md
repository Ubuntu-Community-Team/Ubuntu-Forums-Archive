---
title: "recomend a distribution"
date: 2007-11-16
forum: Other OS Talk
---

### Post by markp1989 on 2007-11-16
im looking to set up a spare computer i have to play videos using geexbox, geexbox has no file management, so i was thinking of using a version of linux to manage all my files.
i  am currently using xubuntu live cd for file management 

i want a distribution that takes up very little hard drive when installed ( preferably under a gig) 

uses kde,xfce or gnome by default, i dont realy like open box, flux box or icewm 

it will basicaly be used to rip dvds, and copy files from usb hdds to the internal hard disk. 

does any one know of a distribution that will meet these requirements?

specs of the pc 
1ghz amd athlon
256mb ram
32mb graphics card
2 x 40gb ide 
1gb cf card with geexbox installed only 60-70mb is used up

any information will be apriciated and i thankyou in advanced

---

### Post by SomeGuyDude on 2007-11-16
I've never tried it, but Fluxbuntu is supposedly great for a computer without a lot of hardware.

---

### Post by new2*buntu on 2007-11-16
> **SomeGuyDude said:**
> I've never tried it, but Fluxbuntu is supposedly great for a computer without a lot of hardware.

I thought he said he doesn't like Fluxbox. I would recommend SAM Linux (it runs snappily even on my old 700mhz P3 with 256 MB RAM) or Linux Mint XFCE (which is based on Xubuntu but has beautiful art and has all multimedia codecs already installed).

---

### Post by markp1989 on 2007-11-16
> **new2*buntu said:**
> I thought he said he doesn't like Fluxbox. I would recommend SAM Linux (it runs snappily even on my old 700mhz P3 with 256 MB RAM) or Linux Mint XFCE (which is based on Xubuntu but has beautiful art and has all multimedia codecs already installed).

thanks for a quick reply, im downloading both of them now so that i can test them to see which one i like best

---

### Post by markp1989 on 2007-11-17
> **new2*buntu said:**
> I thought he said he doesn't like Fluxbox. I would recommend SAM Linux (it runs snappily even on my old 700mhz P3 with 256 MB RAM) or Linux Mint XFCE (which is based on Xubuntu but has beautiful art and has all multimedia codecs already installed).

i decided on linux mint, its grate

---

### Post by mivo on 2007-11-17
Mint with KDE installed uses under one gig?

---

### Post by markp1989 on 2007-11-17
> **mivo said:**
> Mint with KDE installed uses under one gig?

im using the xfce mint 
no it doesnt us under a gig, but it works well and does what i want it to do

it uses about 2 gig

---

### Post by mivo on 2007-11-17
**nods** Thanks! I was curious because most "full" distros I have seen use between 2-3 GB, so I wondered. :)

---

### Post by vishzilla on 2007-11-17
Linux Mint XFCE

---

### Post by Flying caveman on 2007-11-17
How about Momonga Linux 2.  Its kinda cute. [http://www.momonga-linux.org/](http://www.momonga-linux.org/)

I'm trying it out in VirtualBox right now and gave it 256MB ram seems fast.  I'm not sure How much hard drive it took up when i installed, but it can vary from minimal install to 2 DVD everything install,  I just choose the standard desktop install.

EDIT: I guess there on 4 already I'm not sure why I downloaded 2

---

### Post by markp1989 on 2007-11-18
i sorted it out now, i used my 1gb cf card, and installed geexbox to it with 1 big partition.

then following this guide, [https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

i created a custom live CD, which contained 

Ubuntu Base install 
XFCE 4
aMSN
ktorrent 
gwget 
thunar 
xdm

which was all i needed, as it will be used to manage files, and the occasional torrent download..

i ended up with an iso 247mb in size, which i extracted the casper folder to the root of the CF card  and added the following to geexbox menu.lst

title ubuntu lite for browsing internet
root (hd0,0)
kernel /casper/vmlinuz boot=casper xforcevesa
initrd /casper/initrd.gz

after booting from the CF card it worked well and did exactly what i wanted, the only thing i would change is a auto mounter, because i am currently manualy mounting the drives every boot up

currently the CF card has about 600mb free, i wonder what i could use that for

EDIT: if anyone wants a copy of the iso for this, just tell me, and i will see if i can find some wear to upload it to

EDIT1: i would also like to know how to stop it asking me to remove the cd and press enter every time i shut it down

---

### Post by markp1989 on 2007-12-03
Bump

---

