---
title: "[SOLVED] Advice on Replacing Gutsy with Hardy"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by Andavane on 2008-11-23
Hi 

I put Hardy on my laptop, a Sony Vaio VGN-S3HP.
main Computer, an old IBM, is running Gutsy.

As the laptop, runs so well I want to upgrade this IBM to Gutsy, particularly as I'm having problems updating some of the items on Gutsy, so feel a change is needed.

On this PC (The IBM) the main drive is running Windows XP which came with the machine; Gutsy is running off a 160 Gb Hard-Drive which sits in the bay which used to house the CD Drive.

Now my query is:

As linux is already installed, do I have to "do" anything about the grub.
I take it I have to boot on the Hardy CD and delete with GParted the partition on which Gutsy sits?

What about the swapfile? Do I need to delete that too so it can make a fresh one? (I think I made an extra swapfile on the laptop when I installed Hardy, replacing Gutsy.

Any thing I need to know or tips much appreciated.

Regards

John

---

### Post by -Zeus- on 2008-11-23
you don't need to touch gparted, or change the swap.

---

### Post by mister_pink on 2008-11-23
Since you only want to go up one release I'd suggest just doing a distribution upgrade. Sure, they dont always work great, but if you decide afterwards to reinstall you haven't lost anything and it could save you a lot of trouble.

If you've got your heart set on a full reinstall then I'd take the time to learn to use the manual partitioning option - I find it a lot more reassuring to have a look at exactly whats going on. You can tell it to use your current / as / again, and format it, and use swap as swap (which it should automatically do anyway).

---

### Post by caljohnsmith on 2008-11-23
About deleting the Gutsy partition, you don't really need to do that because you can simply specify the Gutsy partition with a mount point of root "/" during the Hardy installation, and also check the box to format the partition, and you should be just fine. And about Grub, if you currently have Grub in the MBR of your Windows internal drive, you don't need to do anything special during the Hardy install since Grub will by default be installed to the MBR of the internal drive. If you are unsure whether you have Grub in the MBR of your internal drive, if you open a terminal (applications > accessories > terminal) and do:
```
sudo fdisk -lu
```
That will list your drives, and sda should be the internal Windows drive. Then do:
```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
If the above command returns "GRUB", you have Grub in the MBR of sda. If the command instead returns "Missing operating system", then you have a Windows MBR in sda. If you would like a bit more specific help, how about posting the results of the above commands, and we can work from there if you want. :)

---

### Post by zvacet on 2008-11-23
@ **Andavane**

First qustion is do you have separate home partition? If you don´t make one following [this]("http://psychocats.s465.sureserver.com/ubuntu/separatehome") guide.
In case that you allready have separate home partition install Hardy on top of Gutsy partition and **don´t format home or swap**.

---

### Post by Andavane on 2008-11-23
> **caljohnsmith said:**
> About deleting the Gutsy partition, you don't really need to do that because you can simply specify the Gutsy partition with a mount point of root "/" during the Hardy installation, and also check the box to format the partition, and you should be just fine. And about Grub, if you currently have Grub in the MBR of your Windows internal drive, you don't need to do anything special during the Hardy install since Grub will by default be installed to the MBR of the internal drive. If you are unsure whether you have Grub in the MBR of your internal drive, if you open a terminal (applications > accessories > terminal) and do:
```
sudo fdisk -lu
```
That will list your drives, and sda should be the internal Windows drive. Then do:
```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
If the above command returns "GRUB", you have Grub in the MBR of sda. If the command instead returns "Missing operating system", then you have a Windows MBR in sda. If you would like a bit more specific help, how about posting the results of the above commands, and we can work from there if you want. :)

Thank you. sudo fdisk -lu returns:

> andavane@andavane-desktop:~$ sudo fdisk -lu
[sudo] password for andavane:

Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78156288 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    41013944    20506941    7  HPFS/NTFS
/dev/sda2        41013945    48612689     3799372+  12  Compaq diagnostics
/dev/sda3        48612690    78156224    14771767+   f  W95 Ext'd (LBA)
/dev/sda5        48612753    56131109     3759178+   b  W95 FAT32
/dev/sda6        64115478    72838709     4361616    7  HPFS/NTFS
/dev/sda7        72838773    78156224     2658726    b  W95 FAT32

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x88086b9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   228428234   114214086   83  Linux
/dev/sdb2       228428235   234436544     3004155    5  Extended
/dev/sdb5       228428298   234436544     3004123+  82  Linux swap / Solaris
andavane@andavane-desktop:~$ 


for the remaining commands I get:
> andavane@andavane-desktop:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 
andavane@andavane-desktop:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings |
> 


I keyed this in twice, leaving off the grep the second time.
Not sure I did right there.

What does this reveal?

---

### Post by Andavane on 2008-11-23
> **zvacet said:**
> @ **Andavane**

First qustion is do you have separate home partition? If you don´t make one following [this]("http://psychocats.s465.sureserver.com/ubuntu/separatehome") guide.
In case that you allready have separate home partition install Hardy on top of Gutsy partition and **don´t format home or swap**.

Thank you.
I tried to make a separate home partition last year and am afraid I ended up hopelessly confused, so ended up going "with the flow."

---

### Post by caljohnsmith on 2008-11-23
OK, like I suspected, you have Grub in the MBR (Master Boot Record) of your Windows sda drive. When you go to install Ubuntu, Grub will by default be reinstalled to the MBR of sda again. So if you're happy with that setup, you don't need to do anything special about where Grub gets installed to. Let us know if you run into any problems. :)

---

### Post by ugm6hr on 2008-11-23
> **Andavane said:**
> Thank you.
I tried to make a separate home partition last year and am afraid I ended up hopelessly confused, so ended up going "with the flow."

If you want to try again, we can help.

---

### Post by Andavane on 2008-11-25
> **caljohnsmith said:**
> OK, like I suspected, you have Grub in the MBR (Master Boot Record) of your Windows sda drive. When you go to install Ubuntu, Grub will by default be reinstalled to the MBR of sda again. So if you're happy with that setup, you don't need to do anything special about where Grub gets installed to. Let us know if you run into any problems. :)

Thank you gentlemen all!
The problem I ran into unexpectedly is that my service provider inadvertently terminated my broadband contract.
They admitted the error and have given "free dialup" yikes what a deal :-(

It looks as though I'll have to put this baby in the freezer until January when I expect all to be back to normal and myself reinstalled (before the operating is... ;))

IO was getting enthusiastic about this project too, but with everything taking ages to load, all maters are painfully slow, I continuie on my laptop.

Thank you all again!

Regards

John

---

