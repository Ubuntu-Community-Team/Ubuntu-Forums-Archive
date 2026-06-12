---
title: "Made GalliumOS live usb on my Ubuntu 18.04LTS laptop, now can't boot"
date: 2020-03-31
forum: New to Ubuntu
---

### Post by laura-4 on 2020-03-31
Boot-Repair Report: [http://paste.ubuntu.com/p/2WXdgs5mQz/](http://paste.ubuntu.com/p/2WXdgs5mQz/)

SITUATION:
[LIST]
[*]Laptop running Ubuntu 18.04 LTS on a 2TB SSD, but laptop also has a separate SSD for windows 10 (i.e., dual boot with grub 2).
[*]Made a live usb of GalliumOS from my laptop while booted to Ubuntu (my primary OS) - successfully created & used to install on a Chromebook
[*]Noticed none of my changes could not be saved on Ubuntu on laptop after this. An error message something about read-only. I stupidly ignored in favor of reboot.
[*]Reboot only went to windows 10.
[*]Rebooted to bios and my normal Ubuntu boot option was gone, replaced with an UEFI option, which I selected, and it booted to GalliumOS live usb, however, the usb that I created for this was not in the machine at the time.
[/LIST]

CONCERNS:
[LIST]
[*]I'm obviously worried I blew away my 2TB SSD with all Ubuntu files.
[*]I'm holding out hope because prior to reboot I had my OS working properly, just not saving
[*]Wonder if I blew away my grub2 by mistake replacing it somehow with GalliumOS live usb info
[/LIST]

WHAT I"VE DONE:
[LIST]
[*]used Ubuntu 18.04 live usb to boot
[*]installed boot-repair
[*]ran boot -repair, however there was no option given to repair, only to create boot-repair report, which is linked to at the beginning of this message.
[*]Only the advanced option on boot-repair gives me something to do. This includes under the MAIN OPTIONS tab, the option to "backup partition tables, bootsectors, and logs" and the option to check "repair file systems".
[*]Under the OTHER OPTIONS tab I have all 5 options checked by default: repair Windows boot file, create a bootinfo summary, upload the report to pastebin, participate to statistics of use, check internet connection.
[/LIST]

I really need advice as to what step to take next to try to restore my system and keep my data intact.

Thanks, in advance, for any help anyone can give me!

Laura

UPDATE: 
* when I tried to view the contents of the drive from the live usb ubuntu, it says "GALLIUMOS" for the drive name, and "Unable to access location, no object for D-Bus interface
* another try from file manager said, "unable to access location, error mounting **/dev/sda1** at /media/ubuntu/GALLIUMOS: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or helper program, or other error.
* similarly, another try from file manager said, "unable to access location, error mounting** /dev/sda3** at /media/ubuntu/GALLIUMOS: wrong fs type, bad option, bad superblock on /dev/sda3, missing codepage or helper program, or other error.
* I looked at the drive from gparted, it says "not mounted". I read in a different thread I could give it a new UUID, but that option was greyed out.

---

### Post by yancek on 2020-03-31
> I'm obviously worried I blew away my 2TB SSD with all Ubuntu files. 

With good reason as that appears to be exactly what you did, writing the Gallium live iso to the hard drive on which you have Ubuntu.  If you look through the boot repair output, you will see references to Gallium in a number of places but none for Ubuntu.  sda2 which is the EFI partition has reference only to Gallium.  You have a separate EFI partition on the functioning windows drive.  I see that sda3, the largest partition on that drive and likely where you had Ubuntu installed is now formatted 'hfsplu' which is a Mac filesystem which would explain the wrong filesystem error you get.  Not sure how that happened?

My only suggestion is to stop using the drive and if possible, back it up and try to recover files from it on the backup using TestDisk. Read the Step by Step instructions carefully before beginning.

[https://www.cgsecurity.org/wiki/TestDisk](https://www.cgsecurity.org/wiki/TestDisk)

---

### Post by laura-4 on 2020-03-31
Thank you for deciphering the report for me. I'm working with testdisk right now and although I see the partitions, it doesn't show any files when I use the 'P' command to see files. However, I used "Intel" as my type of drive. Perhaps since you say it looks to be Mac formatted, I should try testdisk with that type of drive selected? Do you think I should consider sending this out to a professional shop to recover? Or continue with testdrive? I appreciate your insight.

---

### Post by yancek on 2020-03-31
I'm not sure how you got an hfsplus filesystem.  You're not using a Mac are you?  You might try the option EFI/GPT as you have EFI partitions on both drives (sda and sdb) with sda being the drive which had Ubuntu.

---

### Post by laura-4 on 2020-03-31
No, not using mac. It's an ASUS windows 10 laptop. I rarely use Windows, but keep it around in case. I've been a primary Ubuntu user for years. I've never had or done anything like this before. I've also tried photorec, but am not seeing any files listed through that program either.
Testdisk says: Can't open filesystem. Filesystem seems damaged. I'm really worried I'm SOL on this one. :(

Oh, and I did try the EFI/GPT option. Same result. And the "Mac" option and the "None" option. All same result.
[IMG]https://blaivas-my.sharepoint.com/:i:/g/personal/laura_blaivas_org/EcaMpvuf_CdCuPmwe4_-RbkBfoGekJCElIeDVSssI80hIA?e=DBbs4B[/IMG][IMG]https://blaivas-my.sharepoint.com/:i:/g/personal/laura_blaivas_org/EcaMpvuf_CdCuPmwe4_-RbkBfoGekJCElIeDVSssI80hIA?e=DBbs4B[/IMG]

---

