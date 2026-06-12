---
title: "INT/HDD turned into EXT/HDD"
date: 2012-12-29
forum: New to Ubuntu
---

### Post by Powned2death on 2012-12-29
Dont know if anybody can help? I have a 500 gb internal and a 300 gb internal hdd. I took the 300 gb and  installed ubuntu and bt5 and enlcosed it in a external hdd case( saxony 2.5 ext case). My laptop is a samsung rv510 it has only one slot for HDD. I'm trying to keep my 500 gb installed in the laptop with win 7 ultimate. I want to be able to boot from the 300gb EXT without having to manually remove drive everytime I wanna switch OS's. which is the reason I enclosed the internal to be external in the first place. The bios menu allows me to set boot priority and it attempts to boot. However sometime it says no OS or other times it says GRUB RESCUE. Tried the grub rescue disk already, but maybe did something wrong. If the Boot record is in there why is not booting? Cant figure it out should'n be that hard to boot an EXT/HDD with two OS'S installed on it? 

BTW I new to Ubuntu , decided to make the switch after the lastest addition of windows and what microsoft plans to do with the market and app based programs. F U bill gates.

---

### Post by oldfred on 2012-12-29
Welcome to the forums.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
Run with external drive plugged in from Ubuntu liveCD or flash drive. Or you can download a full repair ISO.


[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Powned2death on 2012-12-30
> **oldfred said:**
> Welcome to the forums.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
Run with external drive plugged in from Ubuntu liveCD or flash drive. Or you can download a full repair ISO.


[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

Thanks for responding!

 I wanted to also add.
Both hdd's work when installed seperately into the laptop internally. Its when I have the win 7 os hdd in the internal slot and the linux , debian setup on the ext/hdd connected through usb port (tried all the ports I have btw).  Thats when I have trouble. I tried the reverse set-up having linux installed internally and win 7 on the ext/hdd. And the grub menu will show a win7 loader but it wont boot the win 7 hdd.  Seems like my laptop wont allow me to have two MBR's of two different OS's.  Additionally. everytime I switch back to win 7( internal slot)it has to restore my start up. So this confirms that linux is changing settings in there.  I performed the boot repair and this is the url #1478046. it wouldn send.

---

### Post by Powned2death on 2012-12-30
> **Powned2death said:**
> Thanks for responding!

 I wanted to also add.
Both hdd's work when installed seperately into the laptop internally. Its when I have the win 7 os hdd in the internal slot and the linux , debian setup on the ext/hdd connected through usb port (tried all the ports I have btw).  Thats when I have trouble. I tried the reverse set-up having linux installed internally and win 7 on the ext/hdd. And the grub menu will show a win7 loader but it wont boot the win 7 hdd.  Seems like my laptop wont allow me to have two MBR's of two different OS's.  Additionally. everytime I switch back to win 7( internal slot)it has to restore my start up. So this confirms that linux is changing settings in there.  I performed the boot repair and this is the url #1478046. it wouldn send. just got a second url# 1478051.

---

### Post by oldfred on 2012-12-30
Clickable  link
[http://paste.ubuntu.com/1478051/](http://paste.ubuntu.com/1478051/)

It only shows one drive and cannot even open any partitions. Is is encrypted or does drive have issues?

Windows is designed to only boot from internal drives, since it is licensed for only one system. So you will not be able to use Windows if an external drive.

If Ubuntu drive boots when an internal drive, boot it and rerun BootInfo from that install. Of course that will not show Windows.

Does your computer allow booting from USB ports. It was about 5 or 6 years ago that BIOS were updated to allow boot from USB port. With my laptop which is 6 years old, I have to have a bootable flash drive installed when powering up so BIOS can see it and no other flash drives installed. 
With my Desktop, I have many USB boot options and my flash drive (or other bootable drives?) only boots from the hard drive choice option, not any USB options.

---

### Post by Powned2death on 2012-12-30
> **oldfred said:**
> Clickable  link
[http://paste.ubuntu.com/1478051/](http://paste.ubuntu.com/1478051/)

It only shows one drive and cannot even open any partitions. Is is encrypted or does drive have issues?

Windows is designed to only boot from internal drives, since it is licensed for only one system. So you will not be able to use Windows if an external drive.

If Ubuntu drive boots when an internal drive, boot it and rerun BootInfo from that install. Of course that will not show Windows.

Does your computer allow booting from USB ports. It was about 5 or 6 years ago that BIOS were updated to allow boot from USB port. With my laptop which is 6 years old, I have to have a bootable flash drive installed when powering up so BIOS can see it and no other flash drives installed. 
With my Desktop, I have many USB boot options and my flash drive (or other bootable drives?) only boots from the hard drive choice option, not any USB options.
 
Not sure what you mean. My BIOS allows me to switch to any order and when it recognizes the HDD it says USB/Mass Storage. Last nite I ran some tutorials on EasyBcd and was able to set-up a menu to select OS's but it still will not boot the linux OS. It just goes to a blank screen. I tried making both partitions of linux the boot drive.  Not sure if I have to switch drives or something (one option is named BOOT) or use easybcd's installed grub file.  Also after a few failed attempts last nite I had to re-install the Linux/Debian back on the ext hdd. It was given me the unrecognizable file system error. I was wondering if I should have installed a usb bootable version to the ext/hdd in a chance thatr it mifht recogize that MBR or grub?

---

### Post by oldfred on 2012-12-30
I do not know about EasyBCD, other than it wants to have you install grub2 in ways not recommended and uses grub4dos to chainload to the grub2 entry.

       [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by Powned2death on 2013-01-03
Hey Oldfred, Thanks again for trying. I was on the right track  based on your lastest links. I was for the past couple of days siwtching out hdd's and had easybd installed to store my boot record for the other drive and was somewhat working. But I eventually lost , win 7 again after using 10.4 bt5 extensively. last nite. I'm gonna try dual booting both hdd's , instead off having just win 7 on one hdd and ubuntu on the other. Maybe if i designate a small portion of the windows drive to ubuntu and the small portion on the ubuntu drive to windows. Maybe I could then switch them out without constant issues. I gonna follow the 3rd link you provided and dual boot both hdd's. I'll be sure to post my success or failure. Beggining to hate windows more and more because of this.LOL

---

### Post by Powned2death on 2013-01-09
[QUOTE=Powned2death;12436195]Hey Oldfred, Thanks again for trying. I was on the right track  based on your lastest links. I was for the past couple of days siwtching out hdd's and had easybd installed to store my boot record for the other drive and was somewhat working. But I eventually lost , win 7 again after using 10.4 bt5 extensively. last nite. I'm gonna try dual booting both hdd's , instead off having just win 7 on one hdd and ubuntu on the other. Maybe if i designate a small portion of the windows drive to ubuntu and the small portion on the ubuntu drive to windows. Maybe I could then switch them out without constant issues. I gonna follow the 3rd link you provided and dual boot both hdd's. I'll be sure to post my success or failure. 

Never really got this to work had to eventually just install win 7 on 500gb and use for my important stuff, but I used bcd progrm to try and save my mbr. Then on the other drive I installed Zorin os and win7 , having windows on first then partioning with windows before installing Zorin. I just have to switch out drives in my laptop.

---

### Post by oldfred on 2013-01-09
Windows is real particular about being only on internal drives. Most Linux systems do not care.  
Windows also works best from Primary partitions and has to boot from a primary partition.

While mostly Vista, its how Windows works even 8 is essentially the same if BIOS/MBR. UEFI is a lot different.
       To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

