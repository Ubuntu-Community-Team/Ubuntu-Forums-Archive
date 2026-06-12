---
title: "My Windows 7 partition is not one of the choices I get with GRUB... after boot-repair"
date: 2014-01-19
forum: New to Ubuntu
---

### Post by phil_c2 on 2014-01-19
Please, I need some assistance to figure this out... I can't boot Windows 7 anymore...... f12 won't work (even though my 640gb boots from some sort  of pseudo raid controller). This all started after I booted from a 12.04  live usb key... and made a 40 gb external useable for an  ubuntu boot device. Everything looked good until the first reboot and GRUB did not offer a Windows 7 boot option!

GRUB does however continue to come up again after boot-repair but Windows 7 is still not a choice.... it  offers 12.04 / 12.04 (failsafe) and strangely enough..........."Other Versions of Linux" as a choice?

Here is the boot-repair report I just made:

[http://paste.ubuntu.com/6783675/](http://paste.ubuntu.com/6783675/)

I also see this message on startup:
"**ATI ID 360 hdio_get_identity_faiied for dev/sdh**"

Looks  as if My main Windows 7 drive is reporting some crazy stuff in that far  right "Free Space Area"! (by the way If it will help things) I am not  using anything below and to the "right"of that "Extended 85 GB"  partition. If that Extended, Logicals, and the oddball Free space needs  to go away, I can delete that and I'll just add that space back  (resize/grow that back) into the main "NTFS" Gateway partition. The  Windows "System Reserved" Windows 7 partition is still showing as  bootable and I can mount the filesystem and read the directories and  open files from within Ubuntu 12.04

[ATTACH=CONFIG]249605[/ATTACH]

This a screen shot of the recently added external 40gb HD... loooks good I think

[ATTACH=CONFIG]249609[/ATTACH]


[ATTACH=CONFIG]249606[/ATTACH]

Don't know what to make of this error
thanks


[ATTACH=CONFIG]249608[/ATTACH]

Thanks for any ideas to go on

---

### Post by carl4926 on 2014-01-19
Is sda2 really a windows boot partition?

Why 16GB swap and why sda5 boot

I'd remove sda5, reduce swap and expand sda7 /home
Then reinstall Ubuntu
removing the extended and swap on sdh
set the mount points for / and /home by using the custom partitioner install
set grub to sda

---

### Post by oldfred on 2014-01-20
Do you really have RAID?
Gparted does not work with RAID as you have to use RAID tools to edit RAID drives.
But if sdh is a standard partitioned drive then you can use gparted on it.

Normally with RAID you install grub to the root of the RAID or /dev/mapper/pdc_dhfijejgei not /dev/sda. And if you need a Windows boot loader on a Windows drive then that should be in  the root of RAID not MBR of drive.

But it looks like  you only have one drive? Or is RAID controller showing it just as one drive. Hardware RAID may show that way.

---

### Post by phil_c2 on 2014-01-20
Is sda2 really a windows boot partition?
### **Yes, it's been this way since I bought the machine new**

Why 16GB swap and why sda5 boot
### **I keep reading that you want double the size of you memory in a swap file (I'm 2 gigs away from having 8gb of ram at this moment)**

### [B]sda4, sda5, sda6, sda7 are all unused... this was where I was going to put Ubuntu but ended up sticking it on an external drive (sdh) the sda5 name (/boot) is just a label I used because i thought the label had to match the purpose of the partition... obviously this is not the case.

[/B]
I'd remove sda5, reduce swap and expand sda7 /home
### [B]Since they are all unused would it be safe for me to just remove sda4, sda5, sda6, sda7 I want these off my primary Windows 7 drive... Making this Windows 7 drive/partition bootable again is my real concern... lots of data/work on that drive $$$ I've backed up the best I can but there is likely some data I've missed and my boss is counting on me to get this figured out. I know I've violated one of the Cardinal rules backup, backup, backup and then backup again just to be sure you've got everything.
[/B]
Then reinstall Ubuntu
### **I will gladly/happily/joyfully reinstall Ubuntu onto my external drive (sdh) once I've disassociated my problem(s) from that Windows 7 drive and made it actually boot windows again. **

removing the extended and swap on sdh
### **This (sdh) is currently the only thing that seems to work well/properly Ubuntu 12.04 is all thats on that drive since Windows 7 is nowhere to be found on GRUB the Ubuntu install boots fine**

set the mount points for / and /home by using the custom partitioner install
### [B]unsure what this means ... please explain
[/B]
set grub to sda
### **Not a scrap of OS or data on sda4, sda5, sda6, sda7 are all unused except of course for the Windows 7 partitions sda1, sda2, sda3.**

Thanks
Phil

---

### Post by phil_c2 on 2014-01-20
Do you really have RAID? Gparted does not work with RAID as you have to use RAID tools to edit RAID drives.
### **Yes, turns out there is a physical raid controller (embedded) on this Gateway motherboard that allows for RAID Arrays (Up to Raid 10 I think) of SATA drives.** **This also would now explain why Fedora 20 would not work at all and kept asking about RAID Arrays in manual partition manager**


But if sdh is a standard partitioned drive then you can use gparted on it.
### **Yup, it's a normal 40GB IDE in a USB 2.0 external chassis and seeems to run Ubuntu 12.04 beautifully**

Normally with RAID you install grub to the root of the RAID or  /dev/mapper/pdc_dhfijejgei not /dev/sda. And if you need a Windows boot  loader on a Windows drive then that should be in  the root of RAID not  MBR of drive.
### [B]Right now I just want to get back to booting that single 640gb SATA drive into Windows 7... RAID is a bit too adventurous for me at this point. Will venture into Ubuntu Server and Network Attached Storage once I really learn my way around the Ubuntu Terminal Commands>_  I did manage to get something called "Yakuake" and "KDE Desktop" Installed... COOL!!! Gorgeous Desktop Interface (KDE) and a hot key Terminal prompt !!!
[/B]
But it looks like  you only have one drive? Or is RAID controller showing it just as one drive. Hardware RAID may show that way.                 
### **Yup, you are correct... (1) single 640gb SATA drive **

[B]### God, I hope I haven't permenantly screwed this machine up.

Thanks
Phil[/B]

---

### Post by oldfred on 2014-01-20
I do not know RAID, but am more confused. 
If hardware is RAID, you need more than one drive even if BIOS sees it as one drive via RAID controller.

I might use Boot-Repair to install a Windows boot loader to the root of the RAID and see if from BIOS it boots Windows.
Use Advanced not auto in Boot-Repair and choose Windows and install Windows boot loader to /dev/mapper/pdc_dhfijejgei, note no number or partition. If RAID controller is not really used and you boot from BIOS then you should install to /dev/sda.

---

### Post by phil_c2 on 2014-01-20
I do not know RAID, but am more confused. If hardware is RAID, you need more than one drive even if BIOS sees it as one drive via RAID controller.
###[B]Just think of RAID as a cousin of SCSI Addressing (Devices, Targets, LUN's (Logical Unit Numbers)) with a level of redundancy (Data Striping) accross multiple drives ...the more drives you have the greater level of redundance and protection you have at your disposal... RAID 0 - 10 ...We did this all the time in Netware and Windows Server Installs 
[/B]
I might use Boot-Repair to install a Windows boot loader to the root of the RAID and see if from BIOS it boots Windows.
Use Advanced not auto in Boot-Repair and choose Windows and install  Windows boot loader to /dev/mapper/pdc_dhfijejgei, note no number or  partition. If RAID controller is not really used and you boot from BIOS  then you should install to /dev/sda.
### [B]Thanks for this!!! Windows Boot Loader!!! I'll scour some more for data to offload, then run the Advanced Repair!

Thanks
Phil
[/B]

---

### Post by phil_c2 on 2014-01-21
[B]OK! It is solved and fixed. Booting Windows 7 as required and even got to do a roll-back to a day before I screwed things up.

1. Yes, I do have an embedded RAID controller chip-set (Gateway Desktop DX4320) that can and will spoof single drives to look like a RAID Array. Took a look at the RAID controller configuration at boot and yes, it is treating this single drive as a RAID Array??? there is also a legacy IDE mode to view multiple SATA drives as single IDE drives... I'll leave it as is and now I know not to muck about with gparted on a RAID controller. Eventually I'll populate that controller with a good number of SATA drives and play with some RAID levels.

2. Since I now knew for a fact that there was never a successful UBUNTU 12.04 install on sda4 (Extended), sda5 (/), sda6 (Swap), and sda7 (/home) ...I just deleted them permanently from the main 640gb drive hanging off that RAID controller.

[ATTACH=CONFIG]249630[/ATTACH]

3. Then I grew/re-sized the "Gateway" Windows 7 partition (sda3) and put that extra space that I originally planned for Ubuntu 12.04 and it is now part of a 580gb Windows 7 partition.

4. I took the suggestion made by "Oldfred" and disconnected my external (working) Ubuntu 12.04 drive and booted from my Live-USB stick and followed this link ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) to get "Boot-Repair" loaded and working from the Live-USB stick.

5. I ran the "Boot-Repair" app and selected the "Advanced Options" I had disconnected the external IDE drive with my working copy of Ubuntu 12.04 before booting from the Live-USB stick, so I was thankfully not presented with any GRUB options. I chose the MBR (Master Boot Record) Options tab and selected...

a: Restore the MBR of: sda (Generic MBR)

b: Partition booted by the MBR: sda2 (Windows7)

I am still unclear why Gateway chose to have a "System Reserved" Bootable 100mb partition on sda2 ... but it was what was there before I started trying load 12.04 on this and I kept it as it was. Logic dictates that sda3 "Gateway" should have been the bootable partition with the Windows 7 system on it... so it has to be something to do with this RAID controller because after the system POST you never see that sda2 bootable partition , you always get presented the "C:" drive "Gateway" partition which technically is "D:" drive. Who cares as long as it works!

6. I ran the repair of the MBR and it re-applied the Windows Boot Loader to sda2 "System Reserved" bootable partition.

7. When I rebooted... (No Live-USB and NO External Drive Connected) it immediately launched into the much loved "The File System of Drive C: Needs to be Repaired" and I knew it was doing it's little drive letter translation thing and was talking about sda3 "Gateway" Non-Bootable partition... Again who cares what type wacky translation this RAID controller is performing on a single 640gb SATA drive as long as it works properly again.

8. Success! I watched it reboot and start Windows 7 normally and it even rolled back as requested to a past "Restore Point" from 5 days ago before I started all of this... Successful Windows 7 Boot!
 
9. I connected my external USB Hard Drive with the Ubuntu 12.04 loaded on it and I will simply press F12 and choose it as my boot device to get into Linux! 

10. [COLOR=#ff0000][I][U]I made numerous errors in all of this to begin with. Chief among them was not BACKING UP MY DATA COMPLETELY and PLAYING AROUND with a production system hard drive. I Also learned that GPARTED should not be used to experiment and learn about Linux Partitioning on a RAID attached drive.
[/U][/I][/COLOR]
Thank you to: "carl4926" and "oldfred" and whoever made "[Boot-Repair]("http://help.ubuntu.com/community/Boot-Repair")"

[/B]

---

### Post by carl4926 on 2014-01-21
Pleased to hear of your success
I had to do a clean install of Windows 7 for a customer yesterday. That was enough for a life time.

---

### Post by oldfred on 2014-01-21
Windows changed to add a 100MB boot partition with Windows 7. Supposedly so you could encrypt main install. The Boot also has the repair/recovery so you may be able to fix the main install partition from the Boot partition. But usually better to have a separate repairCD or flash drive anyway.

Windows always requires a chkdsk after any partition size change. It has partition size info in the Windows NTFS PBR - partition boot sector that must match partition table.

---

