---
title: "Preparing Hard Disk Drive for Dual Boot"
date: 2013-09-24
forum: New to Ubuntu
---

### Post by suomalainen on 2013-09-24
Hi Ubunteros!

I got a 160GB HDD that I want to prepare for dual booting.

Can I do the following

1. Create a partion for Windows XP in NTFS (40GB)
2. Create a partion for Ubuntu 12.04 in ext 4 (40 GB)
3. Create a partion for where data can be stored and shared between Ubuntu and Windows in NTFS (80 GB)

OR

Should I:

1. Install Windows XP first on entire disk
2. Install Ubuntu 12.04 next
 BUT HOW CAN I THEN CREATE 80 GB partion where data can be stored and shared between both o/s?

How would you do this?


Thank you

---

### Post by whitesmith on 2013-09-24
Removed as duplicate of post below.

---

### Post by whitesmith on 2013-09-24
Windows is greedy. It wants the entire HDD during an install, so I would go with #1. Of course, modifications are always possible later, albeit troublesome, so #2 is doable as well

---

### Post by ant2 on 2013-09-24
I am assuming you don't have UEFI bios.

I would:
1. Install XP to entire disk.
2. From within XP use a Windows partitioning tool to shrink the XP partition by enough room for Ubuntu and an 80 GB shared partition and create unused space (i.e. 120 GB).
3. Boot XP again to check everything works OK.
4. Boot from Ubuntu DVD/USB check your hardware works OK with Ubuntu. Then install Ubuntu into the unused space. This should create a dual boot XP/Ubuntu environment.
 5. Boot into Ubuntu and use Gparted partitioning tool to shrink your Ubuntu partition by 80GB. Then create an NTFS partition with the 80GB free space you have created.

---

### Post by oldfred on 2013-09-24
If you use gparted to create a NTFS primary partition with the boot flag, XP should just install to that partition. Some with newer Windows had to reformat as part of the install of Windows.

---

### Post by whitesmith on 2013-09-24
> **oldfred said:**
> Some with newer Windows had to reformat as part of the install of Windows.Good point and the basis of my recommendation. Also there can be issues with non-MBR formatting. Has that also been your observation?

---

### Post by oldfred on 2013-09-24
Windows only boots from gpt partitioned drives with UEFI and XP does not work with gpt partitioning nor UEFI. 

I have XP on a MBR(msdos) partitioned drive and Ubuntu on a gpt partitioned drive and that works just fine. Windows does not read Linux formatted partitions any way so it does not even know about the gpt drive.

Part of the issue of XP vs Vista/7/8 is that NTFS is different. The PBR or partition boot sector with XP includes instructions to boot with ntldr where with newer Windows the NTFS PBR has instructions to boot with bootmgr and other internal PBR structure differences.

---

### Post by vicsar on 2013-09-24
Just for the sake of learning (and not messing up your entire system) I suggest you do the follwoing:

This is very important 
[COLOR=#ff0000]***_Before you try anything please BACKUP your important data otherwise you could regret your decisions._***[/COLOR]

**First:**
A.) Download and install Virtual box from here: [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)
B.) Create a virtual Windows machine, once VirtualBox is installed you will see this is very simple to do. Just explore the application and, if needed, read the documentation.

**Then:**
1.) Install XP to the Virtual Machine.
2.) Restart but this time let the virtual machine boot from the Ubuntu image located here: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
3.) Install Ubuntu and when asked choose the "Install systems side-by-side" option. This should create a dual boot XP/Ubuntu environment.

All of the above is very easy to accomplish and I extremely recommend taking this approach before you try it before working on the real machine. When you feel comfortable following the steps mentioned above then you are ready to begin experimenting on your physical mahine.

I cannot stress this enough:
***_Before you try anything please BACKUP your important data otherwise you could regret your decisions._***

---

### Post by Impavidus on 2013-09-25
+1 to oldfred (as always)

You can boot from your Ubuntu live disk and run in trial mode. You'll find a program called **gparted**. You can use gparted to format your drive. Use MBR partitioning and create
- a 40GB primary NTFS partition with boot flag for Windows. It may be best to make this the first partition on the drive.
- a 40GB ext4 partition for Ubuntu
- a ca. 80GB NTFS partition for shared data
- a small swap partition, about one or two times your RAM, depending on the exact size of your RAM and whether you want to hibernate.
The last three partitions can be either primary partitions or logical partitions in an extended partition. Using logical partitions gives some flexibiliy in case you want to add new partitions later.

Then reboot using your XP installation disk and install XP on the 40GB NTFS partition. Reboot using the Ubuntu live disk, install, choose manual partitioning ("something else") and install to the 40GB ext4 partition, selecting a nice mountpoint for the 80GB shared data partition.

---

