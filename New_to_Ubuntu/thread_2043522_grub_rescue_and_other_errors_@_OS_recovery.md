---
title: "grub rescue and other errors @ OS recovery"
date: 2012-08-16
forum: New to Ubuntu
---

### Post by linespace on 2012-08-16
Hi there,

My problem is in part similar to what has been  described in another thread, but the solutions there unfortunately did  not work for me. So, here it goes: I installed Ubuntu 12.04 LTS alongside  Windows XP on a notebook that previously had a single partition (meaning  I re-partitioned during the Ubuntu installation). This was a quick fix  to Windows not working properly and me not having the recovery CD for it around or much time for proper backup. 
When I did get the Windows  XP recovery CD, I decided to run it and well, made the mistake to choose  recovery on the whole harddrive. And this is where I am stuck, as cannot get any operating system on the laptop now. 
Ubuntu was deleted and after the  phase of pre-installation, when the laptop rebooted to complete the  Windows installation, I got the screen reading
`error: no such partition
grub rescue> `

While  I was running the recovery CD I got other errors (eg. related to  partition table) that were automatically fixed by the installer. I also  got the persistent following error:
`Boot Sector Write
VIRUS: Continue (Y/N)?`

_What did not work was_:
- putting the Ubuntu liveCD back in: no response whatsoever
- making and putting in the BootRepair Disk with the download from Ubuntu website: same, no response 
- making and putting in the [Ubuntu-Secure-Remix]("https://help.ubuntu.com/community/UbuntuSecureRemix") CD: same, no response
- typing commands after `grub rescue` such as `setroot= (hd0,0)`: anything I typed would be an unknown command
- restoring the Windows XP bootloader: my recovery CD actually does not have the option restore or repair. 
[It`s a pair of Windows XPH CDs made especially for my old Asus notebook- 2004- and the only options I get are: 1) MS-DOS with CD Rom support; 2-4) Recover Windows XP to first partition/ entire HD/ entire HD with 2 partitions]

- I also tried to run a Kasperski Rescue Disk, but also not response. 

At this point it seems I have 2 problems: 
***_1 _***Maybe  there is a virus in BIOS (my laptop was freezing and had unstable  internet connectivity both in Windows and Ubuntu + the virus message  during recovery)
***_2 _***Because I deleted Ubuntu and messed up the grub, I cannot install any OS on the laptop. 

Perhaps  the 2nd problem comes first as I got no idea how to deal with viruses  having no OS...so here is where I am first in need of help. 

Any  ideas? I would be really happy to be able to work this out, as I got no  other computer nor can I afford to buy one at the moment.
My aim is  to get to the point where I can run a Rescue Disk (Kasperski) or- if I  can install Windows- run some virus scans (OTL, MBAM) to see whether my  problems with the OS were caused by a hardware fault or by a virus...  and hopefully to fix the laptop in the end if it is `just` a virus. 

Many thanks in advance!

---

### Post by linespace on 2012-08-17
so i guess that didn`t work...

---

