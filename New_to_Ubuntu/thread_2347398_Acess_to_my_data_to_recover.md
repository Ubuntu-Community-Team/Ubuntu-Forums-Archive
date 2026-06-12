---
title: "Acess to my data to recover"
date: 2016-12-24
forum: New to Ubuntu
---

### Post by matt910 on 2016-12-24
Hello,

my system crashed and I can't boot Windows 10 x64 from my Lenovo Yoga 2 Pro anymore and the Windows Recovery doesn't work either. I have tried to start to recover Windows from a USB flash drive but it doesn't load. Idk what to do anymore. Ubuntu doesn't let me on the disk to get my files off it. I don't even know how I could reinstall Windows, if I want to install Ubuntu I get an error so it is only possible to run it on the USB flash drive. Never had that before...

How could I get acess to the disk? And is it normal that Ubuntu started from the USB flash drive is running damn slowly and freezing all the time?
When I can run it somehow on the Laptop I try to copy the error shown when I want to get on the disk.

I really would appreciate if someone could guide me trhough that to recover my files if possible.

All the best and merry christmas,
matt9

---

### Post by matt910 on 2016-12-24
Here is the message


Error mounting /dev/sda7 at /media/ubuntu/LENOVO: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999" "/dev/sda7" "/media/ubuntu/LENOVO"' exited with non-zero exit status 13: $MFTMirr does not match $MFT (record 3).
Failed to mount '/dev/sda7': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

---

### Post by arochester on 2016-12-24
You might look at something like [http://www.alandmoore.com/blog/2012/02/03/recovering-data-from-a-pc-a-guide-for-not-computer-people/#more-273](http://www.alandmoore.com/blog/2012/02/03/recovering-data-from-a-pc-a-guide-for-not-computer-people/#more-273)

---

### Post by Geoffrey_Arndt on 2016-12-24
Pls to provide more data on how system became hosed . . . and, what version of Ubuntu Live media.   This is needed to have a better idea if you have a Software or Hardware related issue.

Also, what specific tools or methods have you used to mount the windows partition?   Have you tried gparted?   Have you tried the disks program?   Have you ensured your Windows system fast/quick boot is turned off (Ubuntu will not access hibernated windows partitions).

Do you have a Windows rescue Disk?    

Is any of your critical data backed up  . . or, . . . if not backed up, is any of it on the cloud with a service like Dropbox?

The more detail you provide, the better odds of getting to root of issue(s).

---

### Post by leunam12 on 2016-12-24
It seems that your hard drive is damaged. Download parted Magic and burn it on a USB stick and run "Disk Health". See what it tells you.

[http://www.majorgeeks.com/files/details/parted_magic.html](http://www.majorgeeks.com/files/details/parted_magic.html)

---

### Post by matt910 on 2016-12-25
Well thank you for that many replays.

I tried Disks on Ubuntu to check the partitions but the essential one for Windows and for my files is not accessable.
I got some files I really need for work on this partition which aren't backed up. They are just on the local disk saved under User/Documents in Windows 10.

I tried to recover Windows with an USB stick where I burned win10, but it didn't start either Windows on the disk nor the windows from the disk where I could do the recovery. It was jsut loading all the time but even after hours it didn't go on to the option screen.

I switched in the BIOS the fast boot off, but it seemed to have no effect. Then I loaded the default setting in the BIOS again.

I tried the sudo nftsfix /dev/sda7 and with other corrupt partitions but i always get as result

Mounting volume.... $MFTMirr does not match $MFT (record 3).
FAILED
Attempting to correct errors....
Processing $MFT and $MFTMirr....
Reading $MFT... OK
Reading $MFTMirr.... OK
Comparing $MFTMirr to $MFT... FAILED
Correctiong differences in $MFT record 3... OK
Processing of $MFT and $MFTMirr completed sucessfully.
Setting required flags on partition.... OK
Going to empty the journal ($LogFile)... OK
$MFTMirr does not match $MFT (record 3).
Remount failed: Imput/Output error


Update: I let run the disk check before Ubuntu started. It found errors in 2 files.

[[img]https://s23.postimg.org/iovq62q0n/20161225_133429.jpg[/img]](https://postimg.org/image/iovq62q0n/)

---

### Post by yancek on 2016-12-25
Can you be more specific about what 'crashed' means with your windows 10?  Exactly what happens when you try to boot it?  What happens when you try to access windows from the usb and what is on the usb?

Ubuntu won't let you access a hibernated system as there is too high a likelihood of corruption.  Same with any Linux system.  This is what the message you posted in post # 2 is telling you.

You indicate you get an error when you try to install Ubuntu but don't indicate what that error is?  To clarify then, do you have any other OS besides windows installed?

Running from a flash drive is expected to be slower than from a hard drive.

---

### Post by Geoffrey_Arndt on 2016-12-25
If there is any way you can download & burn a CD/DVD with "_**Parted Magic**_" . . . it has some additional tools to recover files on damaged disks.   Note (the current version of Parted Magic) requires a small fee for download access ($9.00) - - but is the best Linux rescue CD (along with Knoppix) that I know of.

I would suggest to keep Windows quick start off in the firmware.

---

### Post by leunam12 on 2016-12-26
If the problem is that the Windows disk is hibernated you can simply mount it read-only or deleting the hiberfile.```
mount -t ntfs-3g -o remove_hiberfile /dev/sda7 /your/mount/point
```
But it seems to me from what you have posted that the hard drive is damaged. Sometimes you can rescue a drive by changing the PCB, other times there is no fix and, if you don't have backups, all you can do is send the drive to a data rescue professional depending on how important the documents are because that kind of service is usually expensive.

---

### Post by matt910 on 2016-12-26
i tried booting Win10 normally and then with the preinstalled recovery option on the Lenovo notebook and I tried to acess the recovery menu with a usb stick where I burned Win10.

Here are my partitions:

[https://s29.postimg.org/919dcjcaf/20161225_135018.jpg](https://s29.postimg.org/919dcjcaf/20161225_135018.jpg)
Here is the screen where it stops during the boot process

[https://s27.postimg.org/cj0j8p9hv/20161226_103415.jpg](https://s27.postimg.org/cj0j8p9hv/20161226_103415.jpg)

Here is my fast boot turned off in the bios, otherwise I don't know where to turn it off (have no access to windows though)

[https://s24.postimg.org/e8l9prtl1/20161226_103515.jpg](https://s24.postimg.org/e8l9prtl1/20161226_103515.jpg)

I now purchased the Parted Magic and am running it on the device.

I started the program test disk under the menu point rescue and got an partition error on the disk where I installed Win10.
What should I do now with Parted Magic?

Thank you for your help so far! I really would appresciate it if we could save my data.

---

### Post by matt910 on 2016-12-26
Here some data. The Basic health check as you can see in the right corner is passed. Does it mean I have a chance to get my data back? I really don't know anything about this data and I have no clue of working with Linux and Parted Magic. I just want my files back...

[[img]https://s29.postimg.org/ebrv5oe9v/20161226_114941.jpg[/img]](https://postimg.org/image/ebrv5oe9v/)

---

### Post by Geoffrey_Arndt on 2016-12-26
Using Parted Magic & TestDisk program . . . this info may be helpful regarding your next step(s).    [URL="http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair"]http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair

[/URL][http://www.cgsecurity.org/wiki/CategoryData_Recovery]("http://www.cgsecurity.org/wiki/Category:Data_Recovery")

---

### Post by matt910 on 2016-12-28
Thank you!

I was able to get my important data off the disk! Amazing \\:D/\\:D/\\:D/

For all who want to know how: I used PARTED MAGIC (yes, I payed the 9$ and it was totally worth it!)
I run the program "TestDisk" which comes by default with the OS and hit "Analyse" -> "Quick Search" -> the disk's partitions are listed. If there are not all listed like it happend to myself you got to choose one and hit "Deeper Search" or "Deep Search".

Never used this program before and it is really simple! I am so glad I could recover my files!

Thanks to all of you who guided me throught this, you're great!

---

### Post by Geoffrey_Arndt on 2016-12-28
Glad it worked out . . . as a service to other readers who will have similar problems in the future . . . it's helpful to mark this thread as "solved" (see "thread tools" option in upper right of page).    Thanks.

---

