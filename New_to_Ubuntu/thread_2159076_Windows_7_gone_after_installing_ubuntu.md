---
title: "Windows 7 gone after installing ubuntu"
date: 2013-07-01
forum: New to Ubuntu
---

### Post by ICEpower22 on 2013-07-01
Hi guys,
I'm very glad to have finally installed ubuntu but I really wanted to keep Windows around because some of the apps I use are not available on Ubuntu. 
I have made a partition and swap partition for linux and installed ubuntu from USB. After install I wanted to enter windows but there was no boot option.
I tried to download Boot Repair and followed the instructions that it gave me, but every time it gave me an error that grub could not be installed on the following devices (list of devices)

I installed gparted and saw that my whole partitioning was gone and all that was left was 750GB only for ubuntu. (At first I had 4 partitions including for ubuntu)

I hope I have been clear about what my problem is. Can somebody explain to me what I did wrong? I hope everything is still there and not formatted (I have my whole school
work on my other partition)

Thank you in advance!

---

### Post by CrystalDreamer59 on 2013-07-01
Hi I had the same problem. Windows 7 doesn't come with restore disk like previous versions of windows. I have a laptop that started out as a windows 7 then I installed Ubuntu and later wanted to go back to windows 7 for a while because the programs weren't as much and as good as windows. What I eventually had to do was go to my laptop manufacture's website and order the windows 7 restore disk for my laptop. Now I can switch between Ubuntu and windows on my laptop whenever I want to. If you tell me the manufacture and model of your computer I can help you with the process.

---

### Post by Gordon Freeman79 on 2013-07-01
That explains why my niece told me she had no Windows disk for her laptop. I wondered what she meant as it was a brand new machine. I have not upgraded Windows since Vista so I'm only learning about these problems now, as I plan a new 64-bit build for gaming. I'm not sure what you did. I will take care setting my HDD up for dual-boot. I've seen quite a few GRUB-related issues on various forums but not had it myself. I installed Ringtail from a USB stick and selected 'alongside Windows' (Vista was already installed) and GRUB loaded fine, with a boot menu to choose the OS.

---

### Post by ICEpower22 on 2013-07-01
Thank you for reply.
My manufacturer is ASUS, but I actually really need my files. Are they gone for sure? Or is there a way to get them back? Also, my laptop had a recovery partition. That is also gone then?

---

### Post by sixsamuraisoldier on 2013-07-01
try the following:
open terminal in linux and type:
sudo apt-get install os-prober

then type:
sudo update-grub

now, does windows 7 show up in grub 2?
if not, try to manually add it to it (google it), then, try to boot it, if it simply returns to grub try this:
go to grub and change the grub windows 7 entry to 

menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {     insmod part_msdos     insmod ntfs     insmod ntldr     set root='(hd0,msdos1)'     search --no-floppy --fs-uuid --set=root 1EA0019AA0017A13     ntldr ($root)/bootmgr }

[FONT=arial narrow][FONT=book antiqua][FONT=tahoma][FONT=trebuchet ms][SIZE=5]then try it if it doesnt work, chances are youre screwed, [SIZE=5]i had this problem also, you should proba[SIZE=5]bly try [SIZE=5]sudo blkid and make a boot info summary, [SIZE=7]I OVERWROTE THE WINDOWS BOOTLOADER ALSO I NEVER GOT IT BACK[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/FONT][/FONT][/FONT][/FONT][FONT=arial][/FONT]

---

### Post by oldfred on 2013-07-01
If you chose the install to the entire drive option, which in [COLOR=#ff0000]RED[/COLOR] says it will overwrite your entire drive, then it is gone. You may be able to use some recovery tools that look for files on drive. Linux is relatively small so it may have only overwritten some of your data. But it is a long slow process.

First check if all partitions are gone & you only have one ext4. **STOP** using hard drive as all activity is overwriting more data and use install live DVD or flash.

First lets confirm you have no NTFS partitions. From terminal in live version:

sudo parted -l

If no NTFS, then you may try testdisk, but since partition info was also overwritten then that probably will not work.
       [URL="https://help.ubuntu.com/community/DataRecovery"]https://help.ubuntu.com/community/DataRecovery
      [/URL]
 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)
    
Photorec just scans drive for anything that looks like a file.

 Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by CrystalDreamer59 on 2013-07-01
For your files you can buy an external hard drive if you don't have one already and copy them to the external hard drive. As for the recovery partition when I restored my laptop back to windows 7 for a while, the restore disk restored the recovery partition.

---

### Post by Kazo Zako on 2013-07-01
Well I had the same experience with HP laptop as there were 4 partitions, to gain space I reformatted HP restore partition and used it for ubuntu but after installation was no boot to anything little research on "google" and I have resolved the issue, and have now dual boot, I am out of town till tonight and details of my "solution" are on home computer - will post in few hours...

OK I have used two tools HIREN's tools CD to recover partition and MBR as grub overwrites windows  and EasyBCD to manage dual boot. It was with windows 7.

---

### Post by Impavidus on 2013-07-02
+1 to oldfred

Stop using your drive and try file recovery. Chances are you can recover a large fraction of your data.

---

### Post by speartip on 2013-07-02
As oldfred has stated you have probably chosen to "use the entire disc" on install.
What you should have done is ticked the "specify partitions manually (advanced)" box and only formatted the partition that you had created for Ubuntu.
[http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html)
The chanced of recovering anything is very slim.
The moral is always backup your important files & folders before installing, just in case.

---

### Post by dannyboy79 on 2013-07-02
it's all down to what YOU choose during the install of ubuntu. Ubuntu didn't do anything you didn't tell it to do. IF you choose "use entire drive" as the install selection then most likely your data is gone BUT as oldfred mentioned, there are a few things you can "try" to get your data back but don't hold your breath.

It's unfortunate that many new users just speed through the installation and don't read everything properly and then they blame Ubuntu for rerasing their previous Windows installation when in fact Ubuntu only did what YOU told it to do.

---

### Post by enduser79 on 2013-07-02
OP:

I've been using this for years to do data recovery on Windows based machines, the less you write to the disk, the better the chances you can recover your Windows partition with all the files.

[http://www.lsoft.net/bootdisk.aspx](http://www.lsoft.net/bootdisk.aspx)

You can use partition recovery to get your Windows 7 partition back, which of course will include all directories/files.

The software can also make a complete backup of a Windows (or other) partition so if things go wrong, you can go back.

I do recommend having a dedicated machines for learning Linux (I am doing the same thing actually), but if you want to use the same machine with other partitions, a backup is great insurance.

---

