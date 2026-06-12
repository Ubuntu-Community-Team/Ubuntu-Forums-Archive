---
title: "&quot;[errno 5] input/output error&quot; installing ubuntu"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by mnemonik on 2008-07-01
Alright I'm sorry I'm being such a nuisance but I think I figured out the partitioning but around 23% in the install it gives me one of two error messages.

The first one is [errno 5] input/ouput error. It then recomends I either burn a new cd, clean it, or clean my cd drive lens. I can't imagine it would be the cd since before installing I checked the integrity and it said it was all go. The other thing it said was that maybe my hard drive was ****** up, and this was what the other error said as well. I am going to shoot myself if the hard drive is messed up, it was working yesterday with XP, why would it all of a sudden be messed up when I'm trying to install ubuntu??? The last thing it recommends is to try installing again in a cooler environment. Well yeasterday it was around 80 degrees so I thought hmmmmm ok and i tried this morning when its gotta be only 60 out. same error.

I'm really trying to give ubuntu a chance but i feel like it is not trying to help me!!! GRRR. sorry.

Thanks so much for putting up with my novice-ism!

[I'm currently burning a new cd on lowest speed]

---

### Post by avtolle on 2008-07-01
Hope that works, but I suggest that you check the md5sum of the iso before burning it, just in case the iso file was corrupted during the download.

---

### Post by mnemonik on 2008-07-01
> **avtolle said:**
> Hope that works, but I suggest that you check the md5sum of the iso before burning it, just in case the iso file was corrupted during the download.

i did, it matched.

---

### Post by ajji on 2008-12-10
and still thr is no solution to Errno5?

---

### Post by Giorgio Clavelli on 2008-12-10
Hi,
Before shooting yourself, read my successful experience (today BTW)
I have come across the same problem (like several others I discovered), while installing Ubuntu 8.10 (official distribution disk sent me by Canonical) on a new desktop (AMD 64 dual, 4Gb ram, etc). 

I actually have been able to previously install Ubunto 8.04 but then decided to try 8.10 with a fresh install.

Also with version 8.04 installation have had similar troubles. I have used both the official Canonical disk first and then a fresh downloaded copy of it and burned several CDs at lower speed, as I read that may have solved the problem. Somehow it worked with 8.04

However yesterday when I tried to install the version 8.10 (again from an official Canonical CD) got Err 5. 
Have done again the whole lot, finding another disk on magazines, burning the ISO at low speed, some voodoo just in case, but nothing. As the PC is new I refused to believe it having faulty components, so after googling a lot this morning, I found a forum's page, where a guy said it solved the err 5 problem by removing part of the RAM modules, from his PC and putting them back after the successful installation.

I tried it and worked very well. 
Note, this doesn't mean the RAM is faulty, but that there may be some slice difference between the modules (in my case, I ordered this PC with 2 extra GBs of RAM and the seller must have matched the RAM spec, but not used the same brand),

Hope this may help you.

Here the page where I found the solution:
[https://bugs.launchpad.net/ubuntu/+bug/245794](https://bugs.launchpad.net/ubuntu/+bug/245794)

---

### Post by gibber9583 on 2008-12-22
I am getting the same error. it errors out at 65%. I have downloaded the installer.iso from 3 sources. Burned on slow speeds many times. I have created a USB flash drive and booted from that as well.


I have tried this across 3 computers now and am getting the same exact error. This ONLY happens when I try to do a full install of Ubuntu (8.10) and not the 'install inside of windows' option. 


I used my flash drive to install inside of windows and that worked on my Lenovo S10 like a charm. However, I did not like the way the disks were partitioned so I decided to do a full install. Boots from the USB just fine but when i run the installer I get this error. I have tried all of the partitioning options and still run into this error repeatedly....

I used a CD to try and install on an older Acer (1GB of ram in 1 slot) and am still running into this error....

It sounds like I am doing something wrong.

---

### Post by bumanie on 2008-12-22
A number of people had this issue with 8.04. There was no clear fix as such, however, things tried that worked for some were;
1) Try a different cd/dvd-rom drive
2) Burn on high quality media such as verbatim
3) Trying the alternate installation cd
Possily a couple of other things that I can't remember.

---

### Post by dakuwan on 2009-01-18
i was having this same problem installing 8.10 x64 and x86. my computer had 4gb of ram (2x2gb). i removed a module and performed the installation without any errors. then i replaced the module and everything is working great. :)

---

### Post by JoLuc on 2009-01-22
Today, I tried to install 8.10 desktop in an vmware virtual machine under Windows XP using VMware® Player 2.5.1 build-126130.

The CD iso (ubuntu-8.10-desktop-i386.iso, 22 Jan 2008) was mounted as a virtual CD-ROM drive, so any burning issues can be neglected as well as memory timing, SCSI or ATA bus timing or connection errors since these are all virtual devices. But still, to the client OS these virtual devices appear as real hardware, eg the CD-ROM is a NEC something, so driver or BIOS incompatibility could be an issue.

Tried several boot options (noacpi nodma etc.), tried it from an empty disk, tried installing from the live system (which runs perfectly), tried manual partitioning instead of the guided scheme, tried it again on a previously partitioned and formatted disk, but I always got the same [Errno 5] input/output error at around 23%.

Next, i will give a try to the alternate CD iso and report back.

---

### Post by JoLuc on 2009-01-22
...oh, and by the way: I also resized the memory as some of you suggested. Result: plugging out virtual RAM modules does not make any difference. Sadly.

---

### Post by JoLuc on 2009-01-22
There we are, Intrepid up and running in a VM under WinXP! For me, using the alternate installation CD (ubuntu-8.10-alternate-i386.iso) also was the solution. Thanks! :-D

---

### Post by rwpage on 2009-02-18
I've been having trouble installing (getting I/O Errno 5) so it seems from what I'm reading to resolve this a lot of people have used the alternate installer. I'll give it a go and see what happens.

Downloading alternate installer now.

---

