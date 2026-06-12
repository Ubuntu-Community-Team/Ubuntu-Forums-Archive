---
title: "[SOLVED] Replacing Vista with Debian - Questions"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by BGFG on 2008-07-31
So i'm currently getting the Debian netinstall via Deluge. Once i copy off my needed files i plan to begin my install. I have a dell inspiron 531/AthlonX2 64 4000+/1 gigRAM 667 mhz. Debian will be installed on the seagate 250 gig that came with the machine. These are my questions:

1- Are BIOS and Firmware updates difficult ? 
- (part of the reason i still have vista is because these are so easy but it's not a good enough reason anymore, difficult or not, I'll  learn)

2- What's your preference of filesystem ? EXT3, Resier, XFS guys, i'd like to hear you and your reasons. I use ext3 in Ubuntu and it's copy speed from my NTFS drive is very impressive, but my video sometimes sticks. My drive is sometimes noisy too.

3- I've read a lot on having a separate partition for HOME. I've also read that Debian distribution updates are very stable and smooth. is a separate partition still advisable ? If so, I'm thinking 50 gigs for the fs. 150 for home and two 20-25 GIG partions for testing. 

Side note;
When i was installing ubuntu, i put grub in the native Ubuntu partition and used EasyBCD to add it to the vista bootloader. Was smoothness itself. I was concerned as to how i'd get Ubuntu to load considering i'm about to wipe vista but in my reading i saw that the debian installer can search for other OS'es and add them to the bootloader. So i'll see how that goes. :) 
Anyone for Lilo ?

Thanks. I'm off to complete copying my docs. Be back here to see what you guys have to say.

laters.

---

### Post by kerry_s on 2008-07-31
1. nada, that depends on how your bios does updates.

2. i always use jfs now, it just never fails me.

3. i use 1 swap and 1 / (root), that's it no messing around trying to resize if for some reason 1 starts to get full. i do backups externally basically just copy my home folder.

also i recommend starting with etch, if you want more up to date just add the lenny/testing repo and dist-upgrade.

the lenny installer is improving but still manages to bone me every time. i have no idea why it's so damn unstable.

net installer, straight install gives you gnome:
[http://cdimage.debian.org/debian-cd/4.0_r4/i386/iso-cd/debian-40r4-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r4/i386/iso-cd/debian-40r4-i386-businesscard.iso)

kde:
[http://cdimage.debian.org/debian-cd/4.0_r4/i386/iso-cd/debian-40r4-i386-kde-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r4/i386/iso-cd/debian-40r4-i386-kde-CD-1.iso)

xfce4:
[http://cdimage.debian.org/debian-cd/4.0_r4/i386/iso-cd/debian-40r4-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r4/i386/iso-cd/debian-40r4-i386-xfce-CD-1.iso)

---

### Post by neurostu on 2008-07-31
1 - Bios upgrades and very easy, but they are also very trecherous. The problem is if you screw up your bios you can BRICK your mobo, which is a nightmare to fix (some Mobo's it isn't possible to fix)

2- No opinion on fs

3- Seperate home partitions are wonderful. I made the switch and it was one of the best decisions i've made.

---

### Post by RequinB4 on 2008-07-31
> **BGFG said:**
> 

3- I've read a lot on having a separate partition for HOME. I've also read that Debian distribution updates are very stable and smooth. is a separate partition still advisable ? If so, I'm thinking 50 gigs for the fs. 150 for home and two 20-25 GIG partions for testing. 


Unless you're planning on installing every program ever created, You can probably decrease your file system size.  The desktop recommended is 10GB, if you have extra set it to 20 or so and forget it.

Highly recommend a seperate /home partition, makes it a hundred times harder to lose your data.

---

### Post by mevets on 2008-07-31
debian is supposed to be able to detect other operating systems. but ubuntu can too. if your only reason for choosing debian is that it will detect other operating systems then its not such a good idea. in my use of debian it never detected ubuntu on another partition. while ubuntu would always detect any operating system on my disk.

---

### Post by BGFG on 2008-07-31
> **mevets said:**
> debian is supposed to be able to detect other operating systems. but ubuntu can too. if your only reason for choosing debian is that it will detect other operating systems then its not such a good idea. in my use of debian it never detected ubuntu on another partition. while ubuntu would always detect any operating system on my disk.

That wasn't my only reason. It just seemed like a nice feature,  :) 

Well I'm currently browsing in Iceweasel :popcorn: Break out the drinks!

Only issue i'm having:
During the install at the point where you select 'components' to install, I used the netinst iso...
(thank god debian-desktop is checked by default) I forgot spacebar was to select an item and hit enter. Then i cursed...
But i'm glad that happened, it took a little under 3 hours to download and install the 652 packages. 
So now i just enabled the Etch Updates Source Repo. and i'm 'completing' the install. Need to get the nvidia driver among other things.

Just so you guys know, I used the /root/Home/swap config in Logical Volume Management, and i stuck with ext3

Thanks for the responses! Any links to HOWTO's on the BIOS and Firmware updates ?

---

### Post by neurostu on 2008-08-01
What is your MOBO? Get the serial number or the model number and just google for it... every bios is different but you will need a 3 1/2 floopy disk and drive.

---

### Post by kerry_s on 2008-08-01
> **neurostu said:**
> What is your MOBO? Get the serial number or the model number and just google for it... every bios is different but you will need a 3 1/2 floopy disk and drive.

some are designed to be installed from a windows os, maybe wine can do it.
also a lot of computers are dumping floppy drives altogether, mine don't have a floppy. :confused:

---

### Post by BGFG on 2008-08-03
Thanks All. Debian installed. Again. Thread Closed.

---

