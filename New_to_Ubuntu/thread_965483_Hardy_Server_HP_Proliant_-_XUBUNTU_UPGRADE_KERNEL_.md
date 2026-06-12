---
title: "Hardy Server HP Proliant - XUBUNTU UPGRADE KERNEL PANIC!"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by redeyejake on 2008-10-31
Hi
Does anyone have a cunning solution for Kernel Panics...?

Recently decided to upgrade (using apt-get) my 'headless' hardy ubuntu server with Xubuntu gui. Had some trouble with disk space but eventually got the whole thing running nicely. But since a simple reboot the whole system went down with this message: "[8.709363] Kernel Panic - not syncing: VFS: Unable to mount root fs on unkown block."

I found some vaguely relevant info on the forum but unfortunately all advice is over my head (to do with the Grub - i believe) and using command line. I'm familiar with the basics of terminal but i can only use this now through the Ubuntu Server Installation CD this terminal is very minimal - ie the 'nano' doesn't work and the 'mount' command is ropey. Also can't seem to access this grub thing this way.

Sorry i'm a bit of a noob - only been using linux for 2/3 months. The server was great and i suppose quite easy for SMB and Apache setup. I was a happy bunny until i decided to make more use of the PC - which was probably too powerful for the basic use i needed. 

Hardware is: HP ProLiant ML110 G5 Server, it has: Xeon 3065 Dual Core Processor 2.33 GHz, 1x1 PC2-6400 unbuffered DDR2 ECC 800MHz, 
HP Embedded 6 Port SATA Controller with embedded RAID (4 ports for HDD - to which i have two 500G SATAs using the embedded RAID and two 250G SATAs using linux software RAID. The disks are a bit complex for me and probably have about 12 partitions over a samba home media and admin network as well as serving a couple of websites (not professional).

Things worth mentioning: I had changed my 'etc/fstab' prior to this happening - mostly because i decided to go all GUI so that i could install 'Veejay' for a theatre project i'm working on. When i tried to install with 'apt-get' i kept getting error messages like 'failing because a pipe was broken' (or something similar - can't remember now). After trawling the forums and googling my nights away i found a plan. With 'fdisk -l' and using 'df -h' discovered that one partition that i don't use, was full and seemed to have stuff leftover from an earlier (failed) installation. I removed this partion from fstab - that particular mount which i believe was something like '#dev/sdd4   /usr   ext3  ' changing this disk to another mount point like 'dev/sdd4   /mnt/docs '. The system did give some error messages but booted eventually then most importantly at the time also gave me the extra space to 'apt-get upgrade' 'apt-get -f install' apt-get install xubuntu-desktop et al. The install worked and i used it for that night, then shut the system down ready to sort fstab out in the morning. Then got the Kernel panic the next morning.

If anyone has any idea what i can do to rescue this that would be marvellous and i thank you in advance for any help. I wish i could be more specific - just quite hard for me to access the system right now and also although i've been using computers for nearly 30 years... don't really know the first thing about UNIX/LINUX.. obviously..

Thanks again in advance

---

### Post by stephanvaningen on 2008-10-31
1/2: Try booting a previous version of the kernel (can be selected by pressing escape at the GRUB-boot-screen)

2/2: If you also can not boot selecting a previous version of the kernel , there's always a possibility to boot via a liveCD or a rescuecd ([http://www.sysresccd.org](http://www.sysresccd.org)) and then do some maintenance tasks on the hard disk (like making some additional free space by moving some objects to a mounted usb device).

?

---

### Post by stephanvaningen on 2008-10-31
The messing in fstab does not give a good feeling though ;-)

One hint: try to make your posts as small and concrete as possible, many people trying to give (volunteer) support here don't have much time and want to help you, but are sometimes discouraged by big posts and lots of reading -- if you understand what I mean? :)

---

### Post by redeyejake on 2008-10-31
Wow thanks Stephen for the super speedy reply. I'm just sitting down to watch 'Monster House' with my daughter for Halloween. Will get onto that later and let you know how it goes. 
Cheers Jake

---

### Post by redeyejake on 2008-10-31
> **stephanvaningen said:**
> The messing in fstab does not give a good feeling though ;-)

Yes i suppose that is what drew me to Linux is i like tinkering... ;)

> One hint: try to make your posts as small and concrete as possible, many people trying to give (volunteer) support here don't have much time and want to help you, but are sometimes discouraged by big posts and lots of reading -- if you understand what I mean? :)

Yes i believe i do. Thanks for the hint, i'll keep it brief in future.

Also thanks a lot for the pointers with Live CD and the link. That is the way i'm going to go. If i can make space on a partition to install the kernel, and keep all my other data as is, then it will be quicker in the long run i'm sure. Plenty of time to learn about Grubs later..:) 

Cheers Stephan, i'll post later to say how it goes.

---

