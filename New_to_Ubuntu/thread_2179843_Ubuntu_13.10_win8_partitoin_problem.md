---
title: "Ubuntu 13.10 win8 partitoin problem"
date: 2013-10-10
forum: New to Ubuntu
---

### Post by Trainer on 2013-10-10
Hello,

Yesterday i tried to install ubuntu 13.10. On my laptop was windwos 8 pre installed. During the installation ubuntu couldn't detect the partitions of my hard drive. So I tried to restart again without ubuntu. This time my pc can not detect any partions andf system any more. I can only boot via usb.
I think there exist a problem with the partition table.

I have a : Lenovo U430 Touch

Had someone the same trouble like me, or can help me?

---

### Post by Kevin McCready on 2013-10-10
It's possible that something went wrong with the boot sector. Have you looked at:
[http://www.troubleshooters.com/linux/grub/grub.htm](http://www.troubleshooters.com/linux/grub/grub.htm)
I found this on some advice: "It's possible that your Linux system installed its boot loader (GRUB, LILO, etc.) in the Master Boot Record (MBR) instead of the partition boot record (PBR)."

---

### Post by Trainer on 2013-10-10
yeah it can be the probelm. 
But when i start ubuntu live i can't find the partitions.
Do you know how to solve it?

---

### Post by theDaveTheRave on 2013-10-10
When you start the live CD open up gparted, are you unable to see the patitions from here also?

The next thing to try is to open a terminal and send the output of
```

ls -al /dev/disk/by-id

```

and post the output

David

---

### Post by Trainer on 2013-10-10
Terminal output

" ls -al /dev/disk/by-id
total 0
drwxr-xr-x 2 root root 240 Oct 10 11:21 .
drwxr-xr-x 6 root root 120 Oct 10 11:21 ..
lrwxrwxrwx 1 root root   9 Oct 10 12:38 ata-ST500LX005-1CW162_W370A9LP -> ../../sda
lrwxrwxrwx 1 root root  10 Oct 10 12:38 ata-ST500LX005-1CW162_W370A9LP-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 Oct 10 11:21 ata-ST500LX005-1CW162_W370A9LP-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 Oct 10 11:21 ata-ST500LX005-1CW162_W370A9LP-part3 -> ../../sda3
lrwxrwxrwx 1 root root   9 Oct 10 12:38 usb-Kingston_DT_101_G2_0014780D087FEBC095DB009E-0:0 -> ../../sdb
lrwxrwxrwx 1 root root  10 Oct 10 12:38 usb-Kingston_DT_101_G2_0014780D087FEBC095DB009E-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root   9 Oct 10 12:38 wwn-0x5000c50069fc2af5 -> ../../sda
lrwxrwxrwx 1 root root  10 Oct 10 12:38 wwn-0x5000c50069fc2af5-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 Oct 10 11:21 wwn-0x5000c50069fc2af5-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 Oct 10 11:21 wwn-0x5000c50069fc2af5-part3 -> ../../sda3
"
[IMG]http://s14.directupload.net/images/131010/xskftjy3.png[/IMG]

---

### Post by theDaveTheRave on 2013-10-10
OK so you have a 1TB HDD (by the looks) which is 

This is split into 3 partitions.

sda1 : 487 GB
sda2 :  457 gb
sda3 : 7.73

The reason that you don't 'see' anything is because they haven't yet been allocated ~ they have no file systems on them.

When you initially did your attempt to install ubuntu did you intend to wipe out the windows partition? If so there are no problems, 

Either way you will then probably want to make some logical partitions of this disk (currently this is what sda1,2 and 3 are), you could just give sda2 and sda3 a file system type and you should then be good to put ubuntu (or any other os) onto them.

What do you want / need to acheive?

David

---

### Post by Trainer on 2013-10-10
no thats wrong. i only have a 500GB Harddisk.
There should exist 3 or 4 partitoins which are NTFS and FAT32 formated.
But now i can't find them. 
They didn't still exist now.

The UEFI Bios also don't find any partitoin. 

I think the partition table is damaged or MBR or something like that.
Can i recover it?

---

### Post by westie457 on 2013-10-10
Hopefully we should be able to recover from this.

At the moment it is essential that you do not write anything to the hard drive to minimise the risk of any more data corruption.
It is safe to continue using your Live USB.

Firstly before any suggestions for fixing this we need a Boot-info Report. Go here and follow the instructions given to get the the URL for the report and post that here.
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

**Do not attempt any repairs. **

They will only complicate matters.

---

### Post by Trainer on 2013-10-10
[IMG]http://s1.directupload.net/images/131010/ct33wghn.png[/IMG]

do you mean this one?

---

### Post by westie457 on 2013-10-10
That is the one; reposted as a link [http://paste.ubuntu.com/6218043/](http://paste.ubuntu.com/6218043/)

IMHO there is hope for this using testdisk.

Using your Live Ubuntu open a terminal type in ```
sudo apt-get install testdisk
``` and hit Enter.

If the terminal returns with something like 'cannot find testdisk' then do this part: Open Software Centre, go to Edit > Software Sources.
In this window check the top 4 options close out  and close SC. Back to the terminal and ```
sudo apt-get update
sudo apt-get install testdisk
```

When testdisk has installed you are nearly good to go.

Spend some time here [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) to familiarise yourself with testdisk and here [http://www.cgsecurity.org/wiki/Running_TestDisk](http://www.cgsecurity.org/wiki/Running_TestDisk) a menu by menu guide.
This might be more helpful. [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

When you get to the Partition-table type selection please take the GPT option.
After a quick search you will then need to select the 'Deeper Search' to find the erased partitions.

On a 500GB drive the search will take approximately 2 hours.

Anything you are unsure of stop and ask for guidance, if possible post screen shots of where you are stuck.

Good Luck

---

### Post by Trainer on 2013-10-10
[IMG]http://s1.directupload.net/images/131010/dhpi93bb.png[/IMG]

After quick search he found the lost partitions. What should I do now?

---

### Post by westie457 on 2013-10-10
To be honest I would continue in to a deeper search to get a full picture of the partition structure. At the moment there is some overlapping of partitions and the data is incomplete. Out of curiosity, what was shown on the previous screen of testdisk? Did it show any partition numbers?

---

### Post by Trainer on 2013-10-10
which partition should i choose for deep scan?

---

### Post by westie457 on 2013-10-10
Using your last screen shot for reference hit Enter to continue. It will start a scan of the whole drive. It does not normally scan a partition.
ATM I am scanning the drive on my other computer to guide you. Do not panic if you do not get a quick response to your posts. my scan is about 50% and has been running for about 40 minutes.

---

### Post by oldfred on 2013-10-10
Is this an Ultrabook? That uses RAID which confuses things greatly. And the standard desktop installer does not have the RAID drivers although Boot-Repair usually adds them to see the partitions, but grub still does not install correctly as it thinks it should install to RAID when you really want it installed to UEFI (not BIOS).
Partitions will be gpt not MBR(msdos) with Windows 8 booting in UEFI mode with secure boot on.

See more info on Ultrabooks in link in my signature.

---

### Post by Trainer on 2013-10-10
ok i finished it
[IMG]http://img5.fotos-hochladen.net/uploads/screenshotfromdf6knjerhx.png[/IMG]

What now?

---

### Post by oldfred on 2013-10-10
Do not use testdisk to rewrite your partitions. You have Intel SRT.

Lots of info on SRT.
  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

### Post by westie457 on 2013-10-10
@ oldfred

Thank you for joining in. That Intel RST was unexpected, however it probably is the reason 'Testdisk' was showing garbage partition info. When I was running it a short while ago my partitions apparently are the Mac HFS file system and the hard drive was in excess of 16 TB in size. Not bad for a 500GB HDD that has never seen a Mac or its OS

@ Trainer
I have just found out that my laptop has Intel RST as well. I also have to admit that I know next to zero about Raid and its workings. I apologise for nearly destroying your system completely through ignorance.

Take heed of oldfred's advice. He really does know what is going on.

I am now going to hide my head in a bucket and do some more reading.

---

### Post by oldfred on 2013-10-10
UEFI with secure boot has greatly complicated installs. With BIOS you only had one choice although sometimes BIOS settings made a difference. Now you may have UEFI with secure boot, UEFI, or BIOS/CSM and they all are somewhat different and often need settings in UEFI/BIOS for an install to work.

Then they implemented the Intel SRT which is not directly supported yet and dual video which nVidia does not directly support on the new Ultrabooks.
So users with Ultrabooks have lots of new issues, but many have managed to work around all of them. But it is not a simple direct install.

---

### Post by Trainer on 2013-10-11
How should i now proceed? Should i recover it with ubuntu or with windows?

I don't find any option to repair my partitoins. How can i do that?

Should i repair the MBR with the WIN8 CD?
with this command "bootrec.exe /fixmbr"?

---

### Post by oldfred on 2013-10-11
With UEFI you do not even use MBR. 
If you go into UEFI menu can choose Windows does it boot? With either secure boot on or with secure boot off?

If not, I think the fixMBR command on UEFI systems does work but it is not MBR that it fixes.

       Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by Trainer on 2013-10-11
i can't go to the UEFI menue. When i boot i only got this.
[IMG]https://fbcdn-sphotos-h-a.akamaihd.net/hphotos-ak-prn2/v/1378465_10151922318013685_253892663_n.jpg?oh=6d725c5370a63e7907b0f8ed16726b8f&oe=525A76F9&__gda__=1381658692_5c3a19412138e8efed54f7d29205457f[/IMG]

Edit: fixMBR doesn't work. The partitions are not still there :(

---

### Post by oldfred on 2013-10-11
That is just showing a network boot.
Do you have secure boot on or off? Does that make a difference?
Your earlier posts showed Windows partitions and if an UltraBook they may not show correctly from Linux as it has the Intel SRT or RAID. 

Did you make a backup of your system before attempting the install of Ubuntu? That would be the easiest way to fix it now.

---

