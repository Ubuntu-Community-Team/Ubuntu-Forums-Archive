---
title: "Booting new install: Invalid Environmental Block"
date: 2012-11-18
forum: New to Ubuntu
---

### Post by jhughs on 2012-11-18
I put a new (refurbished) 250GB disk in an old Dell 4550 Dimension and loaded Ubuntu.
Everything seems to be working fine but I get the following warning when booting up:
"Error: invalid environmental block.
Press any key to continue..."

I checked with gparted and all looked well.
Ran boot repair but nothing seemed to change.

Below is the report link.
But, if this is nothing to worry about I'll just let it go, but if I should fix it then now would be the easiest time to do it (I can wipe everything out at start over again if needed).

[http://paste2.org/p/2492765](http://paste2.org/p/2492765)

---

### Post by oldfred on 2012-11-19
As a quick test.

Use gparted and shrink your sda1 to less than 100GB. We have seen some installs whether BIOS setting or grub bug we are not sure. We do find a separate /boot inside the first 100GB works. And often just having a smaller / (root) partition will all the boot files nearer the front of the drive works.

I usually suggest a smaller 25GB / (root) partition and separate /home or data partition(s)  for the rest of the drive.

What mode is BIOS in for drive access. AHCI is preferred for newer systems. Otherwise large or LBA but not IDE nor RAID. Also fast boot or quick boot setting can cause issues.

---

### Post by YannBuntu on 2012-11-19
(for information, here is why BR didn't warn about the boot files located too far: [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/1080729](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/1080729) , i'll workaround it by double-check with parted ;) )

**@jhughs:** please could you run Boot-Repair from a recent Ubuntu (or Ubuntu-Secure) disk, and indicate the new URL that will appear?

---

### Post by jhughs on 2012-11-20
Thank you both.
Well, boot repair appears to have done what it was supposed to.  Unfortunately I did not.  I neglected to add the /boot label the first time through so may have possibly installed grub in two places.

If there's not an easier way to clean it up I may just start from scratch and be a bit more careful next time.

Here are the boot info links:
http:/paste2.org/p/2495361   <<< shrank partition but didn't label /boot
http:/paste2.org/p/2495515
http:/paste2.org/p/2495626

---

### Post by oldfred on 2012-11-20
The issue has been boot files beyond the 100GB point on drive. So adding a /boot at the end does not help, they still are far from start of drive.

Is BIOS set to AHCI?

---

### Post by YannBuntu on 2012-11-20
> **oldfred said:**
> The issue has been boot files beyond the 100GB point on drive. So adding a /boot at the end does not help, they still are far from start of drive.

+1 . The separate /boot is not needed.
Please could you:
1) run Boot-Repair --> Advanced options --> GRUB location tab --> UNTICK "Separate /boot" --> Apply, 
2) tell us the new URL that will appear
3) reboot the pc and indicate what you observe

Also, please could you boot an Ubuntu12.10 (or 12.04) disk, choose "Try Ubuntu", install Boot-Repair in it [this way]("https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu"), then run Boot-Repair --> Create BootInfo, and tell me the URL?

---

### Post by jhughs on 2012-11-20
Thank you both.  Seems to boot fine but sluggish once up.
First I owe a couple responses to oldfred:
1) Fast Boot is disabled
2) IDE is my only choice (this is an old Dell 4550).

YannBuntu - here are the two bootinfos.  The first is after running boot info with unticked separate boot.  The second after booting with livedisk Ubuntu 12.10:

[http://paste2.org/p/2499418](http://paste2.org/p/2499418)
[http://paste.ubuntu.com/1373800](http://paste.ubuntu.com/1373800)

---

### Post by YannBuntu on 2012-11-21
> **jhughs said:**
> [http://paste2.org/p/2499418](http://paste2.org/p/2499418)
[http://paste.ubuntu.com/1373800](http://paste.ubuntu.com/1373800)

ok, so now your boot files are correctly located at the start of the disk.
You can delete the /grub folder in sda3 if you want.

Now what do you observe when booting the computer? can you access Ubuntu?

---

### Post by jhughs on 2012-11-21
Thanks.  Yes, boots up to Ubuntu fine (although now seems sluggish... didn't notice that before), but since this issue is fixed I'm marking this solved.

---

### Post by YannBuntu on 2012-11-21
ok, then the problem was the 100GB limitation. Please could you login to your Launchpad account (create one if you haven't yet), go to this bgu report: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1030887](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1030887) , and click on "Does this bug affect you?" --> Yes.

---

