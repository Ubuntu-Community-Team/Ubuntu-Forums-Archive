---
title: "Installed Ubuntu 17.10, now GRUB loads Windows 10 to blinking cursor"
date: 2017-12-09
forum: New to Ubuntu
---

### Post by cart0181 on 2017-12-09
**[Installed Ubuntu 17.10, now GRUB loads Windows 10 to blinking cursor]("https://askubuntu.com/questions/984010/installed-ubuntu-17-10-now-grub-loads-windows-10-to-blinking-cursor")**


  Total noob with Ubuntu here, so bear with me please.


  My goal is to dual-boot Ubuntu and Windows 10. 


  I have an SSD, a 10k rpm drive, and 2 other storage drives in the system.


  I installed from a bootable USB flash drive and selected the option  to install Ubuntu alongside Windows after I first went into the do  "Something Else" menu. From there I *tried* to re-partition my SSD to make room for Ubuntu. That's probably where I messed something up. 


  I tried a bunch of things with the Windows 10 Recovery USB to no avail. Then I tried Boot-Repair from Ubuntu but it didn't change anything.



  I posted the **Boot-Info** to Pastebin [URL="https://pastebin.com/wcCa6ZkP"]Here

[/URL]

  Will someone *please* check it out and let me know what I'm doing wrong. How can I get back into Windows 10 without reinstalling?


  I have an older motherboard so I think it just has a standard BIOS,  no UEFI if that has anything to do with this. It's a GA-890FXA-UD5. I  did not take notice of my Windows 10 Fast Boot setting before  installing.

---

### Post by oldfred on 2017-12-09
It is your fast boot setting in Windows. It leaves it hibernated and then the Linux NTFS driver will not mount nor grub boot hibernated Windows.

From report:
Windows is hibernated, refused to mount

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 
    
You will need to temporarily reinstall a Windows or Windows type boot loader to the MBR to directly boot Windows. Then after you turn off fast start up, reinstall grub to MBR.

Since Windows on updates will often turn fast start up, and you have more than one drive, I might install grub to the MBR of one of the other drives. Then you can boot grub from that drive and keep Windows boot loader on SSD. Grub does not have to be on same drive, although in many cases better.
Then if you need to directly boot Windows you can from BIOS, and not have to go thru the hassle of switching boot loaders in MBR.

---

### Post by cart0181 on 2017-12-09
Thanks so much for the quick reply! I had waited for 4 days without reply on a different forum. I really appreciate this.

I'm glad it seems like you know what is going on here. 

As I said in the OP, I did try a bunch of things with the Windows RE USB flash drive. I know at one point I did /fixmbr and /fixboot but then I read somewhere that those are just for Vista and earlier and so I ran something else more complicated I can't recall atm involving /nt60.
So, I'm afraid I'd like a little more instruction please on how I should go about "temporarily reinstalling a Windows or Windows type boot loader to the MBR" as you suggest. Sorry for my newbie-ness. I've lived inside Windows my whole career and I'm not a coder so I'm weak in this area.

---

### Post by oldfred on 2017-12-09
I believe all versions of Windows use same commands. Even newest UEFI may use same commands, but actual fix is different.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
Windows screenshots:
[http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on](http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on)
BIOS remove Ubuntu with Windows 10 recovery drive
[http://www.everydaylinuxuser.com/2016/06/how-to-remove-ubuntu-from-dual-boot.html](http://www.everydaylinuxuser.com/2016/06/how-to-remove-ubuntu-from-dual-boot.html)

---

### Post by leunam12 on 2017-12-11
You may try this: boot ubuntu and run ```
ntfsfix /dev/sdXY
```where X and Y are the letter and number identifiers for the hibernated partition.

---

### Post by cart0181 on 2018-01-06
I tried running ntfsfix /dev/sda2 and it returns the following:
tim@tim-GA-890FXA-UD5:~$ ntfsfix /dev/sda2
Mounting volume... Error opening '/dev/sda2': Permission denied
FAILED
Attempting to correct errors... Error opening '/dev/sda2': Permission denied
FAILED
Failed to startup volume: Permission denied
Error opening '/dev/sda2': Permission denied
Volume is corrupt. You should run chkdsk.

---

### Post by cart0181 on 2018-01-06
Ok, I tried the instructions as you posted here:
[http://www.everydaylinuxuser.com/2016/06/how-to-remove-ubuntu-from-dual-boo.html](http://www.everydaylinuxuser.com/2016/06/how-to-remove-ubuntu-from-dual-boo.html)

but all I get is back to a back screen with blinking cursor again. I&#8217;m reinstalling Ubuntu right now because that is the only way I know how to get back to a working system. I&#8217;m typing this on my iPhone. Yikes. In the future, is there an easier way to reload the Grub MBR using the install media?

---

### Post by oldfred on 2018-01-06
You ran Boot-Repair, that will reinstall grub.
Often best not to use auto fix, but use the  advanced options and maybe totally reinstall grub.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

Also second link in post #4.

---

### Post by cart0181 on 2018-01-06
OK, thanks. I'll have to try and find an extra flash drive for Boot-Repair.

Back to my original problem, I still can't access Windows... blinking cursor on black screen.

---

### Post by LostFarmer on 2018-01-06
remove sdb and see if it boots.  

Looking at the 'boot-info-script'  
 ```
line #971     -xdump -n512 -C /dev/sdb1  
 line # 549   -Unknown MBR on /dev/sdb  
 Line  # 131  --/dev/sdb1    *              0   586,064,110   586,064,111   7 NTFS / exFAT / HPFS  
```
 has the hdd with sector 0 containing both the Volume Boot Record and the MBR.  Can never happen and do not know how MS Windows would deal with it.  Have no idea how you did it unless you manual edited the hdd data.

---

### Post by cart0181 on 2018-01-06
Thank you for looking at the boot-info, LostFarmer. I wonder if what you see there has something to do with my old Windows install before I added my SSD.
When you say remove, do you mean physically unplug it from the mainboard, or can I remove it from the boot loader somehow? Sorry, I'm very new to this part of computing.

---

### Post by LostFarmer on 2018-01-06
> do you mean physically unplug it from the mainboard Yes, remove power or data cable will do. 

I have never seen nor do I know how MS Windows would install on a non partitioned hdd.   Looks like  the hdd was not partitioned (no MBR) but then linux made a MBR.  Have only seen USB sticks formated with no MBR.  Did you install Windows on to that hdd or copy the OS to it ?

---

### Post by cart0181 on 2018-01-06
I believe it was Windows 7 that I got a free upgrade to Windows 10. I suppose it is possible that I imaged it on with Acronis at one point. That would have been way back when I upgraded to the WD VelociRaptor drive.

---

### Post by oldfred on 2018-01-06
You are showing two Windows installs.
The Windows boot partition is sda1 as it has bootmgr & BCD.
And then you have winload.exe in sda2 & sdb1 (labeled old C drive).
But only by looking at the BCD can you tell what or which Windows is booted.
And you cannot open the BCD from Linux, you need your Windows repair disk.
You may be able to install a Windows boot loader into MBR, and use f8 when directly booting Windows. You then could run Windows chkdsk from that.
Otherwise you need a Windows repair disk.

 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by cart0181 on 2018-01-07
> **LostFarmer said:**
> Yes, remove power or data cable will do. 

Ok! The problem is solved!!! :D  I unplugged all 3 extra storage drives and just kept the SSD connected. Then I was still able to load Grub and Ubuntu so I figured I would try Boot-Repair again and that fixed it this time. I guess having the extra drives must have confused Boot-Repair, especially because I had an old Windows install on one of them. I didn't do the automatic repair btw. But I pretty much kept the default options, I just asked it to boot Windows as the default, but that change didn't seem to take. 

So it looks like I'm pretty much where I wanted to be at this point. I can dual-boot Windows 10 and Ubuntu 17 so this is great. I did disable FastStartup as soon as I entered Windows too btw. The only tweaks I'd like to make now are:

1. Eliminate erroneous Windows 10 entry in Grub on sda1 - only the Windows on sda2 seems to work, not sure why that is...

2. Set Windows as the default boot option in Grub

3. Change the Grub timeout to 2 seconds so as not to slow down my boot time by much.

---

