---
title: "grub rescue error at reinstalling Windows"
date: 2012-08-17
forum: New to Ubuntu
---

### Post by linespace on 2012-08-17
Hi,

I am unable to install/ recover any operating system on my notebook after running a Windows recovery that deleted Ubuntu. 
So in short, when the  laptop rebooted to complete the  Windows installation, I got a black screen  reading
 `error: no such partition
grub rescue> `

_What I tried to do to solve this and **did not work **was_:
- putting the Ubuntu liveCD in: no response whatsoever
- making and putting in the BootRepair Disk CD: same, no response 
- making and putting in the [Ubuntu-Secure-Remix]("https://help.ubuntu.com/community/UbuntuSecureRemix") CD: same, no response
- typing commands after `grub rescue` such as `setroot= (hd0,0)`: anything I typed would be an unknown command
- restoring the Windows XP bootloader: my recovery CD actually does not have the option restore or repair. 
[It`s a pair of Windows XPH CDs made especially for my old Asus  notebook- 2004- and the only options I get are: 1) MS-DOS with CD Rom  support; 2-4) Recover Windows XP to first partition/ entire HD/ entire  HD with 2 partitions]

- I also tried to run a Kasperski Rescue Disk, but also not response. 

Any  ideas? 

Because I had some problems with both of my operating systems, I need to determine whether I have a virus or a hardware problem. So my aim is  to get to the point where I can run a Rescue Disk (Kasperski)  or- if I  can install an OS- run some virus scans (OTL, MBAM)

Many thanks in advance!

---

### Post by mastablasta on 2012-08-17
you need to get to recovery console with windows cd. i think you get there if you initiate install an then select R
 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)
 
asuming oyu have the correct boot order set and liveCD still fails to boot you could also try with live USB instead of CD.

---

