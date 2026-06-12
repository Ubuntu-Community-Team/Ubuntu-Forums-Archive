---
title: "Ubuntu 8.04 wont boot!"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by amc6987 on 2008-11-06
Hey guys,

I have been using Hardy Heron for about two months now and it has been working great. Today I tried booting it on my laptop but the following comes up:

find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst

Error 15: File not found

Press any key to continue...

When I press any key, I get a list of entries that looks like this:

find /ubuntu/disks/boot/grub/menu.lst
find /ubuntu/install/boot/grub/menu.lst
find /menu.lst
find /boot/grub/menu.lst
find /grub/menu.lst
commandline
reboot
halt

I tried doing some research online and found that maybe my partitions are not in order and I have to change it to hd(0,1), but I couldnt figure out where to change it. I've heard people having problems with this when they first try to boot ubuntu, but I have been using it for a while now. Can anyone help me out? Thanks

btw my other OS that is partitioned is VISTA.

---

### Post by Therion on 2008-11-06
Maybe this thread will help?

[http://ubuntuforums.org/showthread.php?t=297261](http://ubuntuforums.org/showthread.php?t=297261)

---

### Post by amc6987 on 2008-11-06
Hi Therion,

I referred to that link, specifically the 9th post by Ralphie and tried both "find /grub/stage1" and "find boot/grub/stage1" after pressing "c" to get to the grub prompt while at that list. Both give me answers of "Error 15: File not found". What should I do now?


Thanks.

---

### Post by mapes12 on 2008-11-06
Hi

Could I please have a look at your configuration i.e. the output from ```
sudo lshw
```

---

### Post by phidia on 2008-11-06
The easiest way to fix this might be to just use the live cd and reinstall grub.
See the guide on doing that [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub").

If you need to get more information on your partitions and the grub settings use "sudo fdisk -l" and copy and paste your /boot/grub/menu.lst

---

### Post by amc6987 on 2008-11-06
Mapes-

I typed that into the grub prompt and got this:

Error 27: Unrecognized command

Should I try that anywhere else?

---

### Post by amc6987 on 2008-11-06
Will I lose all my settings and files if I do reinstall grub?

---

### Post by caljohnsmith on 2008-11-06
Since you are using a Wubi install of Ubuntu, Wubi uses Grub4DOS instead of the Grub that comes with a dedicated Ubuntu partition; therefore reinstalling Grub via the Live CD is unfortunately not going to help you. Have you looked first in your Windows for the C:\ubuntu\install\boot\grub\menu.lst file? And if it exists, does it have the Ubuntu entries in it or is it empty?

---

### Post by amc6987 on 2008-11-06
> **caljohnsmith said:**
> Since you are using a Wubi install of Ubuntu, Wubi uses Grub4DOS instead of the Grub that comes with a dedicated Ubuntu partition; therefore reinstalling Grub via the Live CD is unfortunately not going to help you. Have you looked first in your Windows for the C:\ubuntu\install\boot\grub\menu.lst file? And if it exists, does it have the Ubuntu entries in it or is it empty?

I went to C:\ubuntu\install\boot\grub and it is empty? Whats the next step?

Btw, how were you able to tell I am using a Wubi install?

Thanks.

---

### Post by caljohnsmith on 2008-11-06
> **amc6987 said:**
> I went to C:\ubuntu\install\boot\grub and it is empty? Whats the next step?

Btw, how were you able to tell I am using a Wubi install?

Thanks.
I could tell you have a Wubi install because for one thing, only Grub4DOS uses the syntax "find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst", and also, a wubi installation puts Ubuntu in the C:\ubuntu folder as referenced in that find command. :)

Do you have a menu.lst in this Windows directory:
```
C:\ubuntu\disks\boot\grub\menu.lst
```
And if so, does it have your Ubuntu entries?

---

### Post by amc6987 on 2008-11-06
I dont have a disks folder in C:\ubuntu, but only docs, install, and winboot folders. I opened C:\ubuntu\winboot and found menu.lst in there, though.

---

### Post by caljohnsmith on 2008-11-06
> **amc6987 said:**
> I dont have a disks folder in C:\ubuntu, but only docs, install, and winboot folders. I opened C:\ubuntu\winboot and found menu.lst in there, though.
I believe your main Ubuntu partition should be located at:
```
C:\ubuntu\disks\root.disk
```
So if you don't have a disks folder, do you have that large root.disk file (your Ubuntu partition) somewhere else in C:\Ubuntu? If you can go to the Vista command line (Windows key + R, then "cmd"), how about doing:
```
cd \ubuntu
dir /A:-D /B /S
dir /A:D /B /S
```
I can't remember which of those two dir commands will recursively list your ubuntu directory, so give them each a try. Please post the output if it works.

---

### Post by amc6987 on 2008-11-06
Alright so cd \ubuntu gets me "C:\ubuntu>"

I did the "dir /A:-D /B /S" command there and got this:


C:\ubuntu\curl_log.txt
C:\ubuntu\metadl_log.txt
C:\ubuntu\Ubuntu.ico
C:\ubuntu\Uninstall-Ubuntu.exe
C:\ubuntu\install\installation.iso
C:\ubuntu\install\boot\initrd.gz
C:\ubuntu\install\boot\vmlinuz
C:\ubuntu\install\custom-installation\hooks\casper-premount.sh
C:\ubuntu\install\custom-installation\hooks\early-command.sh
C:\ubuntu\install\custom-installation\hooks\failure-command.sh
C:\ubuntu\install\custom-installation\hooks\success-command.sh
C:\ubuntu\winboot\menu.lst
C:\ubuntu\winboot\wubildr
C:\ubuntu\winboot\wubildr.exe
C:\ubuntu\winboot\wubildr.mbr


Doing "dir /A:D /B /S" gets me:

C:\ubuntu\docs
C:\ubuntu\install
C:\ubuntu\winboot
C:\ubuntu\install\boot
C:\ubuntu\install\custom-installation
C:\ubuntu\boot\grub
C:\ubuntu\install\custom-installation\hooks
C:\ubuntu\install\custom-installation\packages


The dir commands are in the same order you gave them to me (the colon D are coming up as smilies haha)

---

### Post by caljohnsmith on 2008-11-06
Well I'm not sure what to say, because I don't see any sign of a root.disk in your C:\ubuntu directory tree. If you right-click on your ubuntu folder in Windows Explorer, select "properties", how big is that folder? It should be at least as big as your Ubuntu partition. It looks like maybe your Ubuntu partition was deleted somehow, but I'm not sure.

---

### Post by amc6987 on 2008-11-06
Its 708 MB.

If the entire partition was deleted, will I have to reinstall and start over?

---

### Post by kansasnoob on 2008-11-06
I personally know of one instance where I'd done a Wubi install on a friends laptop and when the battery died they ended up with the same situation as a "power outage" on a desktop:

> Hibernation is not supported under Wubi, moreover Wubi filesystem is more vulnerable to hard-reboots (turning off the power) and power outages than a normal filesystem, so try to avoid unplugging the power. An Ubuntu installation to a dedicated partition provides a filesystem that is more robust and can better tolerate such events.

That comes from:

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

---

### Post by caljohnsmith on 2008-11-07
> **amc6987 said:**
> Its 708 MB.

If the entire partition was deleted, will I have to reinstall and start over?
Unfortunately, it sounds like you may have to. How big was your Ubuntu partition? I would try using the search function in Windows Explorer to see if you can find any large files that are the size of your Ubuntu partition, and also search for "root.disk". Also, maybe there's a possibility that one of your antivirus/antimalware programs mistakenly identified the Ubuntu partition as a threat, and quarantined the file somewhere. Do you have any idea of what you might have done in Windows (or what Windows might have done) that could have deleted or moved the Ubuntu partition root.disk file?

---

### Post by amc6987 on 2008-11-07
> **caljohnsmith said:**
> Unfortunately, it sounds like you may have to. How big was your Ubuntu partition? I would try using the search function in Windows Explorer to see if you can find any large files that are the size of your Ubuntu partition, and also search for "root.disk". Also, maybe there's a possibility that one of your antivirus/antimalware programs mistakenly identified the Ubuntu partition as a threat, and quarantined the file somewhere. Do you have any idea of what you might have done in Windows (or what Windows might have done) that could have deleted or moved the Ubuntu partition root.disk file?

It was 20 gigs. I did search for root.disk but nothing is coming up. I haven't been using Windows at all and have no idea why the partition could be moved.

Also, this is related but another problem: Ever since I partitioned my harddrive, I could never pick up any wireless internet on my Windows Vista. Also, I could no longer open up any of my old word/excel files on Windows. Any idea why this is?

---

