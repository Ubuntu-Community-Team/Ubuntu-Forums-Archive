---
title: "having trouble installing ubunt 18.04"
date: 2018-05-26
forum: New to Ubuntu
---

### Post by silveralex2 on 2018-05-26
well i took some pictures to illustrate my point

[IMG]https://drive.google.com/open?id=1TOLbJeAcRUKYyyxrQYiCwGunQsmFw4a9[/IMG]
[https://drive.google.com/open?id=1diQbKMc9Mu7by3AUfdhixB2A0ibpOpAc](https://drive.google.com/open?id=1diQbKMc9Mu7by3AUfdhixB2A0ibpOpAc)
 so i would partition it like that like so
[IMG]https://drive.google.com/open?id=1P9R2EmLT9wlVURJZTTwe1TIgfANEZy8U[/IMG]https://drive.google.com/open?id=1P9R2EmLT9wlVURJZTTwe1TIgfANEZy8U
and then it would do that for a while
[IMG]https://drive.google.com/open?id=1qAkkCMxlgi9Xv-zTMhv3_z3zICGVCmrz[/IMG]https://drive.google.com/open?id=1qAkkCMxlgi9Xv-zTMhv3_z3zICGVCmrz
 then that error message would appear
[IMG]https://drive.google.com/open?id=1MXqk_FxA5qk2-d5AUR_rZ2dgThBWjwzR[/IMG]https://drive.google.com/open?id=1MXqk_FxA5qk2-d5AUR_rZ2dgThBWjwzR
and then after i clicked "OK" it would do that so what should i do please help:confused:

---

### Post by bijayalaxmi1808 on 2018-05-27
Is there anything else on the disk before you start a fresh installation?
It seems OK from the allocations you have made.

From my limited knowledge I can think that the MBR can have only record of 4 partitions. Other left out space cannot be allocated.
Is there an extra partition already present before you install Ubuntu?

What is the efi partition in sdb3 of 50 MB only?
If it is not required delete and merge to home partition.

If nothing works I will suggest you to start fresh, meaning clean the whole disk and make a re partition structure..
I mean, that's what I do when I am installing an Ubuntu and face a problem.

If not wait for a Ubuntu expert to answer you in the right direction.

I don't see any log information on the screenshot to get some idea on this at least!

---

### Post by howefield on 2018-05-27
Feel free to post your images within your post rather than linking to an external site, help others to help you.

---

### Post by bijayalaxmi1808 on 2018-05-27
I totally agree with howefield.
Each time visiting each of the link was of a bit pain and then come back to see what the exact post says about each of these images.

---

### Post by silveralex2 on 2018-05-27
they will not show when i try to post them

---

### Post by UltimateCat on 2018-05-29
Hi:

If you are trying to install Ubuntu alongside of Windows you will first have to shrink your Windows partition in order to have room for Linux.
Do do that look in Disk Management.

You will need at least a 25 GB ext 4 partition to install Ubuntu and a 1 GB linux swap partition for your installation.

Make sure you install the bootloader to the MBR (master boot recorord)

Good Luck with your install.:D

---

### Post by UltimateCat on 2018-05-29
The first link implies that you have another drive on that pc. 

Generally Linux will install as the default to /dev/sda. The screenshot said /sdb which indicates a second drive.

The second link shows that the installer was trying to create an ext 4 partition and it failed.
In this case you may want to manually create your partitions during this install.

The third screenshot is just an ad for help and support.

Create a ext 4 partition and make it at least 25 GB. Than create a 1 GB linux-swap partition and than tell the installer to write to disk.
Make sure you install the bootloader to the disk in which you are installing to and to the MBR.

---

### Post by bijayalaxmi1808 on 2018-05-30
I don't agree that Linux will install as a default to the /dev/sda

It is possible that I have some OS on /dev/sda and some other OS on /dev/sdb and I can dual boot successfully if I install the GRUB on the /dev/sda because that would be the boot partition at that moment.

Make sure you limit the number of partition on the /dev/sdb to only 4 partitions.
Looks like **partition #4** failed meaning it **is the partition number 5 in reality** (that's what I think).

Also select the device **/dev/sda** to **install the boot loader**.

So that you can dual boot alongside Windows or other OS on your system.
If you select /dev/sdb as the boot loader installation location while installing Ubuntu then you need to boot to this drive manually to boot into Ubuntu all the time.

I hope I am clear enough to explain.

---

### Post by Impavidus on 2018-05-30
Is there one hard drive in that computer or more? Bios or uefi? Mbr or gpt partitions? Is there another system already installed? Do you plan to add another OS later? You've opted for manual partitioning, but haven't told us how you want to use your partitions. The information on your screenshot is incomplete and somewhat atypical.

The forum should allow to to add pictures as attachment to your post.

---

