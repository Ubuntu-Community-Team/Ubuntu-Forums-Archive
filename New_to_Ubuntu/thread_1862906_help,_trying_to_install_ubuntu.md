---
title: "help, trying to install ubuntu"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by R_bd_23 on 2011-10-17
i wanted to install ubuntu using flash disk (team project btw)i downloaded the ubuntu and install it to a flash drive. it turned out ok when i used it as a trial on my Desktop computer which is runing on win7 (btw again, you can actually use ubuntu OS even if you didnt install it yet). but when i tried to install it to a newly formatted,partitioned, and installed winXP computer,, well it wont boot from the flash drive. i tried to look at it in the BIOS config and i cant see the "removable disk"option in the first boot, but the comp can read it when i open it on winXP, that means that there is no problem in the flash drive. but i remembered about the BIOS config.. i tried it many time but still get the same results..

---

### Post by nothingspecial on 2011-10-17
Moved to Absolute Beginner Talk.

---

### Post by mastablasta on 2011-10-17
well it may be that BIOS doens't recognise it . i have similar issue with one of the USB disks. options you have now are:
 
use a different USB disk
create a LiveCD and install from that
use PLOP boot manager to boot from USB (for example if oyu have floppy drive oyu can just install PLOP on floppy and then use it to boot from USB)
 
install GRUB to disk first and then use it to boot the USB (i think it would work) - for advanced users only i guess...

---

### Post by R_bd_23 on 2011-10-17
> **mastablasta said:**
> well it may be that BIOS doens't recognise it . i have similar issue with one of the USB disks. options you have now are:
 
use a different USB disk
create a LiveCD and install from that
use PLOP boot manager to boot from USB (for example if oyu have floppy drive oyu can just install PLOP on floppy and then use it to boot from USB)
 
install GRUB to disk first and then use it to boot the USB (i think it would work) - for advanced users only i guess...

the USB works..and i actually want to continue doing the installation with USB out of curiosity.. soo using a liveCD aint an option..

Im using an old motherboard btw.. and some say its because of that reason why i cant install it..

i read about GRUB.. but i really have no clue about it.. and they say its used when you dual boot.. which is what im doing.. ahahah.. im soo screwed.. XD

---

### Post by yndesai on 2011-10-17
If you are not able to use liveCD I do not think your BIOS will be supporting booting from the USB. 

Can you post the make and version of your BOIS and also your hardware details. (Motherboard, processor as min)

---

### Post by R_bd_23 on 2011-10-17
> **yndesai said:**
> If you are not able to use liveCD I do not think your BIOS will be supporting booting from the USB. 

Can you post the make and version of your BOIS and also your hardware details. (Motherboard, processor as min)

the comp is not with me at the moment.. but the motherboard is.. (p4vmmr2) i forgot the manufacturer.. sorry this is all that i know right now..

---

### Post by mastablasta on 2011-10-17
old motherboard might not be able to boot form new USB keys (as you've found out). an option is to try to flash and upgrade the BIOS if you know how.
 
but i would try PLOP in your case which is designed exactly for your problem (boto form old maschines). you can install it to hard disk and during linux install just overwire it with grub.: [http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)
 
>  
Write mbr loader only
[INDENT]A small program (the loader) is required in the MBR to start the boot manager. Operating systems like Windows XP are writing during the installation their own small program into the MBR. If you install Windows XP after the boot manager, then Windows XP will start instead of the boot manager, because the loader is overwritten with the program from Windows XP. To setup that the boot manager starts before Windows XP you have to use Write mbr loader only. Write mbr loader only
[/INDENT]
 
or this:
 
**>  Harddisk install using the Windows boot menu (NT, 2K, XP, VISTA, Win7)**> 
 
Download the current boot manager [plpbt-5.0.13.zip]("http://download.plop.at/files/bootmngr/plpbt-5.0.13.zip"). Extract the zip file. Open the folder Windows. You will find the batch program InstallToMBR. Run it as administrator in VISTA/WIN7 (right mouse click on the file and choose "Run as administrator"). The batch creates an entry in your windows boot menu called "Install the Plop Boot Manager to the MBR". When you reboot, then use the entry to install the Plop Boot Manager to the mbr. 
 
To remove the entry from the windows boot menu run the program c:\plop\plpbt4win. Use "l" to list all entries. Remove the entry with "r ID". ID is the number you have seen with "l". See [here]("http://www.plop.at/en/bootmanager.html#plpbt4win") for more infos to plpbt4win. 
 
Note: plpgenbtldr and contig are no longer required.


---

### Post by 11jmb on 2011-10-17
> **mastablasta said:**
> an option is to try to flash and upgrade the BIOS if you know how.


It should be noted that this is the easiest way to brick your computer

---

### Post by undecim on 2011-10-17
> **11jmb said:**
> It should be noted that this is the easiest way to brick your computer

This. If your power goes out while the BIOS is flashing, your computer becomes slightly less useful than a paperweight.

---

### Post by Mark Phelps on 2011-10-17
It's unlikely that any "P4"-era motherboard includes the option to boot from USB in its BIOS.  And, while an upgrade MIGHT include that, unless there are release notes for the upgrade, and it specifically mentions adding the option to boot from USB, then it's most likely NOT going to work.

Also, when I booted a newer motherboard recently from a USB stick, oddly enough, it showed the USB stick as "B:", that's right, "B:".

But really, I seriously doubt that a P4-era motherboard is going to boot from USB as BIOS updated for them stopped years ago.

---

### Post by mastablasta on 2011-10-18
Yes flashing BIOS is no trivial matter but it is not so scary either. If the upgrade is made in a good way then it is no different than upgrading a programme (ok you would need to maybe move a jumper to clear the previous version). And sometimes it might surprise you what an upgraded BIOS can do. I managed to install a 1.6Ghz Celeron (or was it 1.3ghz) on a P2 motherboard using a special hardware interface and new,upgraded BIOS. worked like a charm. added 512 MB to it and it happilly ran the Win98 until i bricked the windows install and decided to put the XP on (along with XP came mobo upgrade), but this upgraded motherboard with Celeron continued to ran happilly on my friends computer.

---

