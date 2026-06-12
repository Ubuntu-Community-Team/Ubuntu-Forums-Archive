---
title: "GRUB borked after Windows 7 Update Attempt"
date: 2016-01-21
forum: New to Ubuntu
---

### Post by tleo2 on 2016-01-21
Hi All,

For well over a year, I have been happily using Ubuntu LTS 14.04 on an Acer Aspire Timeline X notebook alongside Windows 7. Whenever I boot the system, I use GRUB to choose which OS I want to load. All was fine until I attempted to use Windows Update a couple of days ago. WU wouldn't download anything, even though there were 28 updates available. I tried rebooting. WU still wouldn't download any updates. I booted into Windows 7 as the Administrator and got a lot of weird error messages as the OS attempted to load before finally shutting the system down. When I once again attempted to reboot, I was immediately kicked into the GRUB Rescue Mode and a "No such partition" message. It seems that GRUB/MBR may have been damaged somewhere along the line. 

Anyway, I used my Ubuntu Live CD and ran boot-repair. Boot-repair reported that it ran successfully and its output is located here:

[http://paste.ubuntu.com/14591371/](http://paste.ubuntu.com/14591371/)

I attempted to reboot the notebook, but I'm getting the following error message:

[http://imgur.com/9YqRXJ4](http://imgur.com/9YqRXJ4)

I am now in uncharted waters, and need some assistance as to how to proceed from here. Obviously, I would like to keep my Ubuntu and Windows 7 installations intact, while repairing any damage to GRUB/MBR.

Thanks!

---

### Post by yancek on 2016-01-21
Which partition was Ubuntu on?  Maybe sda3?  You now show the first 3 partitions as windows, the fourth an Extended and the fifth is swap so no Ubuntu.  No boot or Grub files show either.  Boot your Ubuntu DVD and try to mount /dev/sda3 to see if you can view any directories/files.

The image you posted to select Repair from windows should put windows code in the MBR as you now have code from the Syslinux bootloader there.  That should allow you to boot windows.  Don't know if Ubuntu is still there, try mounting and post the results.

---

### Post by oldfred on 2016-01-21
Windows major updates for ages have a bug where a Linux logical partition is not written back to partition table. When you started update, it lost the Linux partition. It still is there, notice space in extended partition between start of extended and start of swap. And restoring that partition & grub usually works to get a working Ubuntu.
But if Windows update failed, you probably will not be able to boot from grub. Grub only boots working Windows. You need to boot a Windows repair CD or flash drive and try to fix Windows. Not sure if directly booting Windows from MBR lets you use f8 to get into internal repair console or not.

All similar issues, most resolved with test disk or parted rescue. 
 [http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080](http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080)
Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)

---

### Post by tleo2 on 2016-01-21
I tried ```
sudo mount /dev/sda3
``` and got

[FONT=courier new]**mount: can't find /dev/sda3 in /etc/fstab and /etc/mtab**[/FONT]

I received the same message when I tried to mount sda4.

I'm pretty sure that Ubuntu was installed on sda4, and that Windows 7 was on sda3. But, I could be mistaken.

---

### Post by tleo2 on 2016-01-21
Thanks for the timely and thoughtful response! I did as you instructed and used a Windows 7 Recovery Disc to repair Windows. It worked like a charm! Now, when I boot the computer, it automatically loads Windows 7. My user accounts and all applications, files, settings, etc. are intact. 

What are my next steps? What I'm asking is, how do I restore access to Ubuntu (as well as get GRUB working as before)??

---

### Post by oldfred on 2016-01-21
See post #3, most of the links are the same, either testdisk or parted rescue.
Then restore grub to MBR.

---

### Post by tleo2 on 2016-01-21
> **oldfred said:**
> See post #3, most of the links are the same, either testdisk or parted rescue.
Then restore grub to MBR.

Okay, I looked at those threads and decided to run parted. It looks like it found the partition, so I added it to the boot table:

[ATTACH=CONFIG]266884[/ATTACH]

I then booted from the Ubuntu Live CD and it looks like the the partition with Linux on it is now showing up as **sda6** :

[ATTACH=CONFIG]266885[/ATTACH]

My next step is to restore grub. I found the thread located here: [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

Is that what I need to do next? And, if so, how do I determine my HDD number??

Thanks again!

---

### Post by yancek on 2016-01-21
Don't use the link you posted as that is 10 years old and using Grub Legacy not Grub2 which is used on current Ubuntu systems.  Nothing in that post will work for you.  Go to the link below which has several ways to reinstall Grub2.  Read through before you start anything and post back if you have problems.

[https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2)

---

### Post by tleo2 on 2016-01-22
> **yancek said:**
> Don't use the link you posted as that is 10 years old and using Grub Legacy not Grub2 which is used on current Ubuntu systems.  Nothing in that post will work for you.  Go to the link below which has several ways to reinstall Grub2.  Read through before you start anything and post back if you have problems.

[https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2)

Thanks! I read through that page and found the grub installation option that applies to my situation.

After booting to the Ubuntu LTS 14.04 Live CD and launching the Terminal, I mounted sda6 using:

```
sudo mount /dev/sda6 /mnt
```

I then attempted to install grub:

```
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```

But I received the following message:

```
Unrecognized option '--boot-directory=/mnt/boot'
```

---

### Post by oldfred on 2016-01-22
Command looks correct. 
Older versions of grub used root not boot, but otherwise the same.

But you started using Boot-Repair and I kinda assumed you would just use it. It is often the easiest way to restore grub.
And it has several ways to restore it if issues. I can do the auto fix, which really is just the same as the commands you ran. But its advanced mode can do a full uninstall/reinstall of grub also. 

And restored partition usually works with just a reinstall of grub, but if issues may need a fsck.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda6 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda6
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda6

---

### Post by tleo2 on 2016-01-24
> **oldfred said:**
> Command looks correct. 
Older versions of grub used root not boot, but otherwise the same.

But you started using Boot-Repair and I kinda assumed you would just use it. It is often the easiest way to restore grub.
And it has several ways to restore it if issues. I can do the auto fix, which really is just the same as the commands you ran. But its advanced mode can do a full uninstall/reinstall of grub also. 

And restored partition usually works with just a reinstall of grub, but if issues may need a fsck.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda6 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda6
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda6

No worries. I ran boot-repair and grub is now back to normal, except I seem to have picked up a Windows 7 loader showing up on sda2 which I don't think I had before. 

Anyway, Ubuntu is back and all of my programs, files, and settings are as they were. Same with Windows 7 (on sda3). 

Thanks so much for the help!!!

EDITED TO ADD:  Almost forgot to post the successful boot-repair output: [http://paste.ubuntu.com/14627887/](http://paste.ubuntu.com/14627887/)

---

### Post by oldfred on 2016-01-24
Many users do not know that the 100MB Windows boot partition is essential & houseclean it. So Boot-Repair copies bootmgr & /Boot/BCD  into main Windows partition as backup.
But then grub2's os-prober finds boot files (it looks for files, not boot flag) and adds another entry into grub menu. 

Probably best just to leave it. But you can manually edit grub's 40_custom with one entry, turn off os-prober, and convert menu to one entry.

---

