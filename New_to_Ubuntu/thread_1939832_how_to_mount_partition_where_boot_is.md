---
title: "how to mount partition where /boot is?"
date: 2012-03-12
forum: New to Ubuntu
---

### Post by Vpc on 2012-03-12
I am using Ubuntu 11.10 on my usb pen drive. I see a black screen after the BIOS/Intel motherboard screen when I try to access my hard drive with 11.10 installed so I am trying to follow these instructions below so I can access the grub menu to make the necessary changes.

> 
There are a few options to control this behaviour that can be set in the file: /etc/default/grub
If you want the menu to display every time, comment out the GRUB_HIDDEN_TIMEOUT setting by putting a '#' in front of it:

    # GRUB_HIDDEN_TIMEOUT=0


You should also ensure the GRUB_TIMEOUT setting has a value greater than or equal to 1:

    GRUB_TIMEOUT=10


If you make any changes to the file, you must run the command:

    sudo update-grub

to ensure changes are picked up.

However, when I run sudo update-grub, I get:
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

I get the same error after ```
sudo mount /dev/sda1 /mnt 
```

How can I fix this?

---

### Post by dino99 on 2012-03-12
open synaptic, then purge all the related grub installed packages
and reinstall grub-pc then
and finally: sudo update-grub

---

### Post by Vpc on 2012-03-12
> **dino99 said:**
> open synaptic, then purge all the related grub installed packages
and reinstall grub-pc then
and finally: sudo update-grub

Can you specify how I would find "all the related grub installed packages" in synaptic i.e. do you suggest I really delete all packages with "grub" in their name?

I also noticed another step suggested here:
[http://ubuntuforums.org/showthread.php?p=8563870](http://ubuntuforums.org/showthread.php?p=8563870)

> **taurus said:**
> If you cannot get into GRUB menu, then you need to boot your machine with the LiveCD.  Then mount the partition where /boot is, and edit /boot/grub/menu.lst.  Change the timeout to some integer.

So would it help to "mount the partition where /boot is" and what would be the command to do that?

---

### Post by Vpc on 2012-03-12
I am using Ubuntu 11.10 on my usb pen drive. I see a black screen after the BIOS/Intel motherboard screen when I try to access my hard drive with 11.10 installed so I am trying to follow these instructions here ****to access the grub menu:
[http://ubuntuforums.org/showthread.php?p=8563870](http://ubuntuforums.org/showthread.php?p=8563870)

> **taurus said:**
> If you cannot get into GRUB menu, then you need to boot your machine with the LiveCD.  Then mount the partition where /boot is, and edit /boot/grub/menu.lst.  Change the timeout to some integer.

How do I "mount the partition where /boot is" i.e. which partition are they referring to and where do I mount it to?

---

### Post by spiky001 on 2012-03-12
Hi   Did grub load, did you get any errors when you booted the machine, Have you any idea what has made it not startup properly, Has the system been working.

---

### Post by raja.genupula on 2012-03-12
hey what you wanna do ? you wanna set GRUB time ? 

for all Grub related operations the best possibility we have with us is Grub Customizer(please eye at signature)

one more link much helpful to you is [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) .

---

### Post by Vpc on 2012-03-12
> **spiky001 said:**
> Hi   Did grub load, did you get any errors when you booted the machine, Have you any idea what has made it not startup properly, Has the system been working.

Because of the problem I described in my first post, I would like to enter the GRUB menu to do the following:

> Press and hold down Shift key from Bios screen until see the Grub menu. Highlight the first entry, press &#8220;e&#8221; to edit it. Navigate to words &#8220;quiet splash&#8221;, delete them and type &#8220;nomodeset&#8221; in their place (without quotes). Press Ctrl + X to continue boot.
Once on the desktop, go to System > Administration > Additional Drivers and activate the recommended drivers and the problem should go away for ever.

---

### Post by spiky001 on 2012-03-12
Can you post the output of ```
sudo fdisk -l
``` From the booted usb drive, this will show what partitions are on the hard drive

---

### Post by sudodus on 2012-03-12
Has your system been working 'live' from the USB drive?

Has your installed system been working before (or is this your first try)?

Maybe you can try boot options according to
[[COLOR="Red"]_https://help.ubuntu.com/community/BootOptions_[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

---

### Post by Vpc on 2012-03-12
> **sudodus said:**
> Has your system been working 'live' from the USB drive?

Has your installed system been working before (or is this your first try)?

Maybe you can try boot options according to
[[COLOR="Red"]_https://help.ubuntu.com/community/BootOptions_[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

Yes it works 'live' from my CD & USB pen drive. I was able to install 10.04.04 on my hard drive but 10.04 was not compatible with my ethernet card or onboard ethernet so installed 11.10 over it using the CD.

> **spiky001 said:**
> Can you post the output of ```
sudo fdisk -l
``` From the booted usb drive, this will show what partitions are on the hard drive

The output:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00007d29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   968429567   484213760   83  Linux
/dev/sda2       968431614   976771071     4169729    5  Extended
/dev/sda5       968431616   976771071     4169728   82  Linux swap / Solaris

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001cddb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    77369039    38684488+  83  Linux
/dev/sdb2        77369040    80292869     1461915    5  Extended
/dev/sdb5        77369103    80292869     1461883+  82  Linux swap / Solaris

Disk /dev/sdc: 8010 MB, 8010194944 bytes
247 heads, 62 sectors/track, 1021 cylinders, total 15644912 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008f6e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          62    15635593     7817766    c  W95 FAT32 (LBA)
```

I've tried:
```
sudo mount /dev/sda1 /mnt
```

But still I get this error I run 'sudo update-grub' after editing /etc/default/grub:
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?)

So which partition should I be mounting and where should I mount it to?

---

### Post by spiky001 on 2012-03-12
Have a look [here]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by oldos2er on 2012-03-12
Threads merged. Please don't start more than one thread for the same question.

---

### Post by sudodus on 2012-03-12
> Yes it works 'live' from my CD & USB pen drive. I was able to install 10.04.04 on my hard drive but 10.04 was not compatible with my ethernet card or onboard ethernet so installed 11.04 over it using the CD.

Before fighting further on, I suggest that you download the iso file of your present version (11.04 or 11.10), make a boot CD or USB drive and test how that works. If there are problems, try the boot options (linked to in a previous post)! It is good to test these things live, because then you know what to expect when you are starting to install the system.

---

### Post by Vpc on 2012-03-12
> **sudodus said:**
> Before fighting further on, I suggest that you download the iso file of your present version (11.04 or 11.10), make a boot CD or USB drive and test how that works. If there are problems, try the boot options (linked to in a previous post)! It is good to test these things live, because then you know what to expect when you are starting to install the system.

Yes I have looked at the boot options link but could not find the answers to my questions. I am using 11.10 live on my USB drive. I want to enter the grub menu to fix a problem with the 11.10 on my hard drive.

> **spiky001 said:**
> Have a look [here]("http://ubuntuforums.org/showthread.php?t=1014708")

I had a look at the link (which is a thread about restoring bootloader) but am I mounting properly? I posted the output you asked for and I am wondering if you have any feedback for it.

---

### Post by spiky001 on 2012-03-12
```
sudo mount /dev/sda1 /mnt 
``````
sudo grub-install --root-directory=/mnt /dev/sda
``````


reboot
sudo update-grub
```

---

### Post by Vpc on 2012-03-12
> **spiky001 said:**
> ```
sudo mount /dev/sda1 /mnt 
``````
sudo grub-install --root-directory=/mnt /dev/sda
``````


reboot
sudo update-grub
```

I ran the code above and still got the same error message when I run 'sudo update-grub'. I am considering the earlier advice below. I didn't try it yet because I was not sure about deleting packages. Especially it seems I would have to delete all packages with 'grub' in the name and then possibly delete the wrong ones.

> **dino99 said:**
> open synaptic, then purge all the related grub installed packages
and reinstall grub-pc then
and finally: sudo update-grub

I will try the Grub Customizer also suggested earlier.

> **raja.genupula said:**
> hey what you wanna do ? you wanna set GRUB time ? 

for all Grub related operations the best possibility we have with us is Grub Customizer(please eye at signature)

one more link much helpful to you is [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) .


Let me know if you have any further feedback.

---

### Post by sudodus on 2012-03-12
> **Vpc said:**
> Because of the problem I described in my first post, I would like to enter the GRUB menu to do the following:

> Press and hold down Shift key from Bios screen until see the Grub menu. Highlight the first entry, press &#8220;e&#8221; to edit it. Navigate to words &#8220;quiet splash&#8221;, delete them and type &#8220;nomodeset&#8221; in their place (without quotes). Press Ctrl + X to continue boot.
 Once on the desktop, go to System > Administration > Additional Drivers and activate the recommended drivers and the problem should go away for ever.

Did you ever do that? At reboot from HDD, 
*'Press and hold down Shift key from Bios screen until see the Grub menu.'* This should work on a PC, but it is different on a Mac.

---

### Post by Vpc on 2012-03-13
> **sudodus said:**
> Did you ever do that? At reboot from HDD, 
*'Press and hold down Shift key from Bios screen until see the Grub menu.'* This should work on a PC, but it is different on a Mac.

No it doesn't work. That's why I'm editing the timeout variable. See my previous posts in this thread.

---

### Post by sudodus on 2012-03-14
What computer is it? Brand, type, version ...

And what is working right now? Sometimes, after changing so many things, we can get lost (not only you, but we, who are far away from your computer). Sometimes we misunderstand each other, sometimes we think the status is what it was at an earlier point.

Finally, referring to post #10 and the output of [FONT="Courier New"][SIZE="3"]sudo fdisk -l[/SIZE][/FONT], please describe the three drives sda, sdb and sdc (what is on each partition)! Are you sure that your current system is on sda?

---

### Post by YannBuntu on 2012-03-14
Hello
please could you provide your [BootInfo URL]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1") ?

---

### Post by Vpc on 2012-03-14
> **YannBuntu said:**
> Hello
please could you provide your [BootInfo URL]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1") ?

Running Boot-Repair (available from the above url) solved the problem. In Boot-Repair I went to Advanced Options->Grub Options and clicked on "Edit GRUB configuration file" setting the timeout variables as stated in my first post and GRUB_CMDLINE_LINUX_DEFAULT="" (removing "quiet splash"). I also checked 'Add a kernel option:" selecting "acpi_osi=" and then clicked Apply. After rebooting, I was able to log into my hard drive.

---

### Post by sudodus on 2012-03-14
Congratulations :KS

And thanks for sharing your solution!

---

