---
title: "Editing menu.lst w/ Vista,XP and Recovery Partitions."
date: 2008-09-04
forum: New to Ubuntu
---

### Post by Lamb579 on 2008-09-04
Let me start by giving you a background on the events that led me to this point.

I have an HP Tx 2000 (Don't Recommend it), which came with Vista Home Premium.  I Used the Ubuntu CD to make a new partition and install Ubuntu to see if I would want make the switch.  I can only get a few things working right in Ubuntu due to my lack of education on Ubuntu and the terminal but more on that later,  For now I had this bright Idea that I could use XP even if I had to give up the tablet features by doing so.  So I created a new partition using the XP CD and I installed XP on the new partition.  I hade to run the Ubuntu CD again to reinstal Grub.  The Problem is that Grub will only recognize Ubuntu and the XP Os on but not the original Vista.


I did fdisk -l and got this:

> Disk /dev/sda: 250.0 GB, 250059350016 bytes

255 heads, 63 sectors/track, 30401 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x47741003




Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1       23383   187821364    7  HPFS/NTFS


Partition 1 does not end on cylinder boundary.

/dev/sda2	  23384         26108      21888562+   f  W95 Ext'd (LBA)

/dev/sda3   	  26109         28657      20474842+  83  Linux

/dev/sda4         28658         30401      14008680    7  HPFS/NTFS

/dev/sda5         23384         26108      21888531    7  HPFS/NTFS




 
And My menu.lst looks like this:
> ## ## End Default Options ##


title		Ubuntu 8.04.1, kernel 2.6.24-19-generic

root		(hd0,2)

kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=496fe8f4-4894-4985-a231-27befdb8a3c7 ro quiet splash 

initrd		/boot/initrd.img-2.6.24-19-generic quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)

root		(hd0,2)

kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=496fe8f4-4894-4985-a231-27befdb8a3c7 ro single

initrd		/boot/initrd.img-2.6.24-19-generic




title		Ubuntu 8.04.1, memtest86+

root		(hd0,2)

kernel		/boot/memtest86+.bin
quiet




### END DEBIAN AUTOMAGIC KERNELS LIST




# This entry automatically added by the Debian installer for a non-linux OS

# on /dev/sda5

tittle          Windows XP (Loader)

root    	(hd0,4)

savedefault        

makeactive

chainloader 	+1




# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1

title		Windows Vista/Longhorn (loader)

root		(hd0,0)

savedefault

makeactive

chainloader	+1




# This entry automatically added by the Debian installer for a non-linux OS

# on /dev/sda2

title		HP Recovery/Longhorn (loader)

root		(hd0,1)
savedefault

makeactive

chainloader	+1







This is after I added the XP entry my self.  BTW, I was able to boot to Vista once but the options seem to be one or the other but I could not have both listed in menu.lst

Thanks in advanced.

---

### Post by ebmelle on 2008-09-04
Suggest taking a look at [http://apcmag.com/how_to_dual_boot_vista_and_xp](http://apcmag.com/how_to_dual_boot_vista_and_xp) etc. Also download EasyBCD.exe to make the selection.  Grub should let you chose Linux or Windows, and EasyBCD which vesion of Windows.

---

### Post by mikewhatever on 2008-09-04
What do you mean by Grub doesn't recognized Vista? Don't you get the 'Windows Vista/Longhorn' entry in the menu?

---

### Post by Lamb579 on 2008-09-04
For: ebmelle - I'll try it and post my results.


For: mikewhatever - If I select the Vista entry it still loads into XP not Vista.

---

### Post by mikewhatever on 2008-09-04
> **Lamb579 said:**
> For: mikewhatever - If I select the Vista entry it still loads into XP not Vista.

So it is in GRUB's menu, and you can select it as a boot option. If you don't get any errors GRUB seems to do its job and the problem is with Vista's bootloader. The entry for Vista clearly points to a different partition, then the for XP. I think you need to check the boot.ini file on sda1. Can you post access it from Ubuntu and post here?

---

### Post by Lamb579 on 2008-09-05
:) Good News: I used EasyBCD and it was so easy to use.  I went to this site:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4") 

I was able to recreate the Vista MBR and used the NeoGrub also but now I have Vista working and Linux has a sub menue where if selected takes me to the 3 default Ubuntu options and all that works just fine.

** Here is the kicker**

Remember I have Vista on C: - HP Recovery on D: - XP on F: (F: while in Vista G: when I used to be in XP):confused: and Linux on its own partition.  So I attempted to add XP in EasyBCD by pointing it to its own partition, where it used to load in G rub before EasyBCD, but it did not work.  The screen reads:  

> Windows Failed to start...

Something about repair Windows with installer CD and error info, 

in bright white letters:

File: \NTLDR

Status: 0xc000000f

:  

So now I need to fix XP  for it to boot from the menu created by EasyBCD.  But for now here are the settings in EasyBCD as of now:

> 
There are a total of 3 entries listed in the Vista Bootloader.
Bootloader Timeout: 30 seconds.
Default OS: Microsoft Windows Vista

Entry #1

Name:  Microsoft Windows Vista
BCD ID:  {current}
Drive:  C:\
Bootloader Path:  \Windows\system32\winload.exe
Windows Directory:  \Windows

Entry #2

Name:  Microsoft Windows
BCD ID:  {50e7f8f7-7acb-11dd-915d-001e683fb485}
Drive:  F:\
Bootloader Path:  \NTLDR

Entry #3

Name:  NeoGrub Bootloader
BCD ID:  {50e7f8f8-7acb-11dd-915d-001e683fb485}
Drive:  C:\
Bootloader Path:  \NST\NeoGrub.mbr

I'll keep you posted.

---

### Post by Lamb579 on 2008-09-05
After visiting the forum at Neosmart Technologies I got my issue resolved 100%.  

This is my posting there:  [http://neosmart.net/forums/showthread.php?p=23647&posted=1#post23647]("http://neosmart.net/forums/showthread.php?p=23647&posted=1#post23647")

All I had to do was change the letter to C: for the location of NTLDR for Win XP to Work.

Vista, Win XP and Linux all working.

Thanks for the help guys.

---

