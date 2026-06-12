---
title: "Can't Open Ubuntu Even After Install"
date: 2015-09-27
forum: New to Ubuntu
---

### Post by vin-cent-ho on 2015-09-27
My computer says "S.M.A.R.T hard drive detects error, suggests backing up" right after my BIOS loads. When I click esc, it should lead me to the login page, but it only shows a black screen and stays that way.
Boot-repair report: [http://paste.ubuntu.com/12590385/](http://paste.ubuntu.com/12590385/)

---

### Post by grahammechanical on 2015-09-27
Would please explain the decisions you made as part of the Ubuntu installation process. I ask because if I am reading the Boot Repair report correctly, Ubuntu is not installed. As I see it, and I may be wrong, sda is the USB drive that you are running Boot Repair from. That would make sdb the drive that Ubuntu should be installed in. And Ubuntu is not there. The partition it should be in (sdb1) is not listed. And that could be because of the hard drive errors.

Boot Repair is offering to repair - filesystems. If you want you can accept the offer. The Ubuntu install disc/USB offers these options

Try Ubuntu without installing
Install Ubuntu
Check disc for defects
Test memory
Boot from first hard disk

We get that menu when we press Enter at the first purple screen. The one with the icons of a human and a keyboard. So, you can use that menu to check the disc for defects. The process might also repair what it can. Then you can try installing Ubuntu again. The Try Ubuntu session will load to a desktop and you can open the Disks utility and that will access the hard drive S.M.A.R.T data and run self-tests if you want further confirmation.

Regards

---

### Post by vin-cent-ho on 2015-09-27
Sorry, I forgot to say that I did install Ubuntu. Then I used GParted to delete it because I couldn't use it.
Edit: Also, the installer crashes now. The first time installing did work, though.
Also I did a memtest and it turned out fine (don't know how this would be relevant though).

---

### Post by yancek on 2015-09-27
So what exactly is the problem?  Are you trying to install Ubuntu again after having just installed and removed it?  Or are you just trying to boot the Ubuntu flash drive to check the hard drive?  Have you set the BIOS boot priority to boot from the flash?   The message you posted in your initial post indicates drive errors which probably need to be repaired.  You obviously won't be able to boot the hard drive as there is no operating system on it.

---

### Post by vin-cent-ho on 2015-09-27
Sorry, I'm new here. Heres a more detailed description:
Originally, I used Windows 7. I decided to install Ubuntu. It was working fine until the screen froze. I clicked the power button to close the computer. After I opened it, the computer said something like "No Operating System found". Afterwards, I tried to reinstall Ubuntu, but it wouldn't work. So I tried to erase all the data on my computer be reformatting my hard drive (since I didn't have permission to delete anything because I was using a bootable usb to fix things). Afterwards, it still didn't work. So I tried basically everything. I tried using GParted to delete partition sdb1. I tried using boot-repair. I tried to use fsck (still have no idea what it does). I even tried to install linux mint. Nothing works.

Oh and I reinstalled Ubuntu, just to see the following error:
"error: attempt to read or write outside of disk "hd 0"
Entering rescue mode...
grub rescue>
"

Now I'm trying to use boot-repair to fix things. Here is the boot-repair report:
[http://paste.ubuntu.com/12591318/](http://paste.ubuntu.com/12591318/)

Edit: Oh, also there's that hard drive error that I mentioned on the first post.
Edit2: [http://paste.ubuntu.com/12591428/](http://paste.ubuntu.com/12591428/) Heres the fixed boot-repair report.
However, last time when it said the computer was fixed it was still broken. I don't know
Edit3: Yup, still broken. The exact same errors. I checked for defects on the disc, and it said that there were 2 files with errors. But that happened to me the last few times I checked for defects, and I used different "discs", or iso files. I used [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) to burn the iso into my usb.
Edit 4: When I boot by the usb, the following lines are shown:
[some_random_number.some_random_number] ACPI PCC Probe fail
[some_random_number.some_random_number] ATA1: COMRESET failed (errno = -16)

---

### Post by vin-cent-ho on 2015-09-27
Hmm... Used a utiltiy called disks. It gave me:
500 GB Hard Disk
/dev/sdb
Model: WDC WD5000LPVT-22G33T0 (01.01A01)
Size: 500 GB (500,107,862,016 bytes)
Partitioning: Master Boot Record
Serial Number: WD-WX11A1337984
Assessment: DISK IS LIKELY TO FAIL SOON (43° C / 109° F)
_Volumes_
(all data about the partitions)

How can I fix the assessment thing?

---

### Post by Bucky Ball on 2015-09-27
> **vin-cent-ho said:**
> "S.M.A.R.T hard drive detects error, suggests backing up"

> **vin-cent-ho said:**
> 
Assessment: DISK IS LIKELY TO FAIL SOON (43° C / 109° F)


Both of which effectively say exactly the same thing: your disk is on the way out. Backup and replace immediately. Try and avoid using that disk directly for anything but backing it up. Boot from live media to backup to external device, if the internal disk will let you access it.

memtest is for testing RAM.

---

### Post by vin-cent-ho on 2015-09-27
So there's no way to fix it but to change the hard drive?
Also, I have no data to backup. I only used Ubuntu for 1 day, then it stopped working.
Edit: One weird thing: My computer still gives me the grub error even though boot-repair should have fixed it.
Edit2: The hard drive error only occurred after I reformatted sdb1. Is there a correlation?

---

### Post by Bucky Ball on 2015-09-27
Probably just coincidence. These things happen.

---

### Post by vin-cent-ho on 2015-09-27
So basically just change a hard disk.

---

