---
title: "Install Failure - Busybox Initramfs - Driver 'sr' needs updating bus_type"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by grahamt2280 on 2008-06-06
Hi all,

I have got problems installing Ubuntu Hardy on to a large hard drive (specifically a Samsung HD300LD 300 Gig).

If I try to do a normal new fresh install, I end up dumped into the Busybox Initramfs text mode, with error text slowly scrolling up the screen. For the exact error text, see (3) below.

I have done a lot of troubleshooting and have conclusively proven to myself (and hopefully to the reader) that it is not a problem with the install media (1), or the hardware(2).

If I use the boot option [F6] and remove the "quiet" and "splash" options, I can the look at the boot text scrolling up the screen. 

The last line of boot text appearing prior to being dumped into the BusyBox/Initramfs error mode is:

sda: <4> Driver 'sr' needs updating - please use bus_type methods

I have read up on Boot options 
[http://help.ubuntu.com/community/BootOptions](http://help.ubuntu.com/community/BootOptions)
and have tried "noacpi", but the same failure still occurs.

So now I ask for help from the community. How do I "update my sr driver", how do I "use bus_type methods" and/or how else should I progress trying to get Ubuntu installed on the 300G HDD?

Thanks in advance.

Graham


(1) It's not a problem with the CD media. 
===========================================

I've tried using 7 different CDs:
	Canonical supplied offical Ubuntu CD
	Downloaded main ubuntu & kubuntu cds
	Downloaded alternate ubuntu & kubuntu cds
	Downloaded LinuxMCE cd 
	Downloaded Mythbuntu cd. 

All media pass the "Check CD for defects" test without problems. 

(2) It's not a problem with the hardware.
=========================================

(i) Ubuntu Hardy installs without problems without onto smaller (e.g. 10 Gig ) harddisks.

(ii) Running Ubuntu Hardy in Live CD mode works well, with a small or even with _no_ hard disk installed. 

I see the Language menu, then the "Cylon bouncing bar", then the Progress Bar climbing to 100% then the normal Ubuntu desktop. 

But if all I do is power off, install the Hard disk, and try again, I see the Cylon bouncing bar then the Error Text.

(iii) Fedora, Windows 2000 & even Ubuntu 6.04 install and work well without problems on this 300G hard disk. n.b. installing 6.04 and then trying to upgrade to Hardy presents it's own severe problems, so that's no an option.

(iv) I have tried this on 5 different PCs, all work well with Ubuntu Hardy & smaller harddisks &/or Fedora/Windows 2k and the large hard disk. In every combination tested, it is only the combination of Ubuntu & the 300G disk that fails.

(3) Here is the exact error text copied from the normal install process.
========================================================================

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [ 58.809162] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 58.580406] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in

[ 58.580451] ata1.00: status { DRDY }
[ 88.676227] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 88.676273] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in

Then the three lines from "status { DRDY }" repeat until I power off.

---

### Post by Francewhoa on 2010-03-11
Same here. **The following worked for me** [http://ubuntuforums.org/showthread.php?p=8952609#post8952609](http://ubuntuforums.org/showthread.php?p=8952609#post8952609)

---

