---
title: "Ubuntu will not boot"
date: 2018-06-12
forum: New to Ubuntu
---

### Post by hardcoretexan on 2018-06-12
I started having problems with firefox freezing up when I went to print in my work matrix, I updated my software and restarted and I got a flashing cursor.
I got back into the loading screen and went through the repair packages, boot loader etc and still no load. I loaded into live and tried the boot repair and got an error(the boot of your pc is in EFI mode but no efi partition was detected. You may want to retry after creating a EFI partition(Fat 32, 100mb-250mb, start of the disk, boot flag).Do you want to continue?

I clicked yes and waited for it to create a partition then it created a boot info script.
I then tried to reinstall Ubuntu but it failed to create a boot loader.
So now I have a 50gb partition and a 447gb partition with my files still on it.

This computer was formatted with ubuntu 16.04 on it and no other operating system.

---

### Post by TheFu on 2018-06-12
Issues like this are usually some sort of hardware failure, IME.  Check the disk, cables, controller for issues. SMART might be useful - any relocated sectors?  CRC errors usually mean a bad SATA cable.

Can you restore from a backup?   Backup religion will make things like this a minor inconvenience, nothing more.

---

### Post by hardcoretexan on 2018-06-12
If it was a bad cable would I still be able to access all my files?

---

### Post by yancek on 2018-06-12
> tried the boot repair and got an error(the boot of your pc is in EFI mode but no efi partition was detected.

Since Ubuntu is the only OS install, that would mean that you booted the Live CD with boot repair in EFI mode but you actually had a Legacy install.  If you had an EFI install, it would have been necessary to have an EFI partition already.  You should have clicked  NO when asked to create an EFI partition now you have an additional problem.  Since you have run boot repair and got the output, is there some reason you did not post the link here so that members more familiar with bootloaders could view it?  That would be your best next step.

---

### Post by hardcoretexan on 2018-06-12
What is the easiest way to link to the file?

---

### Post by TheFu on 2018-06-12
> **hardcoretexan said:**
> If it was a bad cable would I still be able to access all my files?

A failing cable sometimes only partially fails. The SMART data will show CRC issues, lots of them.  Look at the SMART data.

---

### Post by yancek on 2018-06-12
> What is the easiest way to link to the file?

Mouse over the icons above your entry box window here until you see one that says link and click it and add the link you got from boot repair.

---

### Post by hardcoretexan on 2018-06-15
[https://paste.ubuntu.com/p/byN9Gnbvrw/](https://paste.ubuntu.com/p/byN9Gnbvrw/)

---

### Post by hardcoretexan on 2018-06-15
[URL="https://paste.ubuntu.com/p/byN9Gnbvrw/"]https://paste.ubuntu.com/p/byN9Gnbvrw/
[/URL]

[https://paste.ubuntu.com/p/8MHFtYvgrY/](https://paste.ubuntu.com/p/8MHFtYvgrY/)

---

### Post by oldfred on 2018-06-15
Boot-Repair does not create partitions, if you want to convert to UEFI with gpt partitioning that will erase entire drive.

Your current install is in BIOS boot mode with MBR(msdos) partitioning.
Best to reboot Boot-Repair in BIOS boot mode and rerun report.

You also need to houseclean old kernels.
       [URL="https://help.ubuntu.com/community/RemoveOldKernels"]https://help.ubuntu.com/community/RemoveOldKernels

[/URL]
 Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
# kernels, shows older also?
dpkg --list | grep linux-image
-s is simulate so you can see what it will do, then run without -s
sudo apt-get -s autoremove 

[URL="https://help.ubuntu.com/community/RemoveOldKernels"]
[/URL]

---

### Post by TheFu on 2018-06-16
Did you ever look at the SMART data for the disks?

---

### Post by hardcoretexan on 2018-06-16
I apologize for being a pain but I went to the above link and I'm more confused than before, could you post the procedure

---

### Post by oldfred on 2018-06-16
You use Disks and in upper right corner the icon has smart status.
All I know is passed or good, but it can run lots of tests.

Attached screenshot is older, but it still is same.

---

