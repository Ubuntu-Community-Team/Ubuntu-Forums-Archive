---
title: "Boot Repair Gone Wrong"
date: 2013-06-25
forum: New to Ubuntu
---

### Post by ferds on 2013-06-25
I installed ubuntu 12.04 in partition with Windows 7 about a month ago, and have been using it mainly for video-editing.

This evening I have begun to have some problems with snowballed. I have been getting a lot of crashes on Kdenlive, but tonight I started getting problems with corrupted files as well. I'm working on a fairly large project and a saved file was lost, leaving me working on a backup version.

I was going along alright redoing my edits, as I had only lost about an hour or so of work, when the system freezed up again. When I went to reboot, it got stuck on loading screens or black screens. So I went back to Windows to try and find a solution. 

I booted from an external drive and ran Boot Repair. This seemed to work, but when I rebooted my dual boot option was gone, and I was taken straight to Windows. 

My Ubuntu partition is still on the hard disk, with all my saved files, but it won't boot. I would very much like to get back into Ubunutu to recover my work. 

FYI, this is my Boot Repair summary: [http://paste.ubuntu.com/5797705/](http://paste.ubuntu.com/5797705/)

---

### Post by fantab on 2013-06-25
You have a WUBI install. Which is installed within Windows. Though you have use a separate partition, yet it works from Windows. Its NOT a true dual boot. 
I am not sure how to fix WUBI installs. My suggestion will be to [Remove WUBI]("https://wiki.ubuntu.com/WubiGuide#Uninstallation") and Install Ubuntu as 'true' dual-boot.

But first you MUST rescue your DATA on /dev/sda5. To do this [download a copy of Ubuntu 12.04 ]("http://www.ubuntu.com/download/desktop")(if your processor supports 64bit then download 64bit Ubuntu), do a [MD5Sum Check]("https://help.ubuntu.com/community/HowToMD5SUM") and burn it to a [**DVD**]("http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows") or [**USB**]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows") from Windows.
Boot with Ubuntu DVD/USB and 'Try Ubuntu without Installing'. Let the desktop load. Open the 'File Browser/explorer' - it will be listed as HOME on the left hand launcher.
In the File Browser, under 'devices' locate your old Ubuntu partition and click on it. It should open. Save everything you want to on, preferably an external disk. 

Once you are able to rescue your data, then you can install Ubuntu directly to the partition you have reserved for it after you have formatted it with ext4.
If you need more help regarding Install then get back here after you have saved your data.

Good Luck....

---

### Post by ferds on 2013-06-25
Ok, I did a lot of reading up and pretty much seem to be back where I started boot-wise. I reset the boot through Windows to the Wubi dual boot, and get the two options at start up.

The problem is that Windows boots fine, while I am back to the same failure to boot Ubuntu. It gets me to the purple screen and freezes up. I did have to force shutdown back when all this first started happening, so maybe that's the issue.

My main goal is to save my files, but I can't get access to them from the live USB boot. All I get are the "boot" and "ubuntu" folders. When I try to mount the Ubuntu partition, it says it is already in use. And when I try to access them from Windows via Ext2explore, the disk doesn't read.

I still have a the full volume of memory being used by the Linux disk, so I think my files are still there. I just can't get access.

---

### Post by ferds on 2013-06-25
I tried again to access the files via live Ubuntu boot, with these commands:

mkdir /mnt/mountpoint
mount /dev/sda? /mnt/mountpoint (you need to find the correct number of your partition here: use fdisk -l)
cd /mnt/mountpoint/home/username (puts you in your home directory)

The first two worked fine, but the last one gives me a reply saying that there is no such file or directory. 

Is that entire drive just gone? I checked it both on Windows and on Gparted and they said it was healthy. Please help, I am losing my mind over this.

---

### Post by Cheesemill on 2013-06-25
Those instructions wont work as you have a Wubi installation instead of a proper dual boot, all of the Ubuntu files live inside a file on the Windows drive rather than their own partition.

Try these instructions instead...
[http://www.thefilipinogeek.com/2012/10/recover-files-from-wubi-installation.html](http://www.thefilipinogeek.com/2012/10/recover-files-from-wubi-installation.html)

---

### Post by ferds on 2013-06-25
Thank you so much! That one did work. 

After I back up, any suggestions on the boot problem?

---

### Post by Cheesemill on 2013-06-25
Personally I would install Ubuntu as a proper dual-boot setup instead of using Wubi.

---

### Post by oldfred on 2013-06-26
From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

      
 HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)

---

