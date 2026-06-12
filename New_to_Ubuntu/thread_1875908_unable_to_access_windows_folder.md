---
title: "unable to access windows folder"
date: 2011-11-05
forum: New to Ubuntu
---

### Post by aditya_lugia on 2011-11-05
hi guys i m new to ubuntu.I m a windows user n a imp windows file crashed.I wanna fix it by accessing the folder from Ubuntu live(mounted in a pen drive).However i see the windows folder empty.Besides my "my documents' folder of windows is shown as empty but it contains atleast 50gb of data.How do i view my windows folder? i have mounted ubuntu 11 and i dont have samba.If i should install samba,do gimme a link

---

### Post by Seb71 on 2011-11-08
For system rescue, Knoppix is a better choice than Ubuntu Live CD. You have read-write access.

---

### Post by Mark Phelps on 2011-11-09
In all versions of Windows since Vista came out, "My Documents" is ALWAYS empty -- because it's nothing more than a soft-link now.  The actual files are stored under C:\Users\<username>\AppData\...
where ... is Local or Roaming. Also, "AppData" is a hidden directory -- which won't bother Ubuntu, but will hide it from view (by default) in Windows.

Also, booting from an Ubuntu LiveCD also gives you read-write access to the Windows partitions by default.

If you're really planning on "fixing" your Windows problems by booting into a Linux CD, then you need to tell us A LOT more about what you intend to do. It's obvious from your comments that you're not familiar with the modern architecture of the Window OS filesystem.

---

### Post by aditya_lugia on 2011-12-03
yeah i m new to the architecture.All i would want is to be able to access the windows folder.Also my hard disk has only one partition where windows is installed.So i dont think i will be able to install ubuntu coz i dont want to format my hard disk.Can u tell me what information do you guys need to further assist me in solving this problem?? i m trying to fix in a netbook with no cd drive.However i can borrow a usb cd drive from my friends if needed.I m have mounted ubuntu 11 on a pen drive.I m sure u guys will need much more than this...let me know. Also can i install knoppix on Ubuntu live??
Basically i have a hal.dll file prob.So hopefully copying and pasting a new file on the existing one wil fix the prob.So i intend to access my windows folder through ubuntu(access the windows/system32) and replace the file

---

### Post by aditya_lugia on 2011-12-03
Also i tried installing ubuntu and in the installation screen is confusing.I want to create a new partition and install ubuntu in the new partition with no loss of data.I would like to create a new partition with the free space available.Wat are the options or procedures to chose??

---

### Post by Mark Phelps on 2011-12-03
If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

### Post by aditya_lugia on 2012-01-01
I am currently running Windows XP service pack 2.Its a netbook so it doesn't support windows 7.My hard disk has no partition( but it does free space upto 70GB).The problem I am facing is that I do not know the procedure to create a new hard disk partition using Ubuntu installation.I am unable to access the hard disk through Windows xp so please guide me in your procedure using Ubuntu only(P.S its mounted on pen drive).
I would be grateful if you could give me a step by step link to create a new partition on the empty space and install Ubuntu 11

---

### Post by GrouchyGaijin on 2012-01-01
> **aditya_lugia said:**
> I am currently running Windows XP service pack 2.Its a netbook so it doesn't support windows 7.My hard disk has no partition( but it does free space upto 70GB).The problem I am facing is that I do not know the procedure to create a new hard disk partition using Ubuntu installation.I am unable to access the hard disk through Windows xp so please guide me in your procedure using Ubuntu only(P.S its mounted on pen drive).
I would be grateful if you could give me a step by step link to create a new partition on the empty space and install Ubuntu 11
Did you make a live USB drive?  How are you going to put Ubuntu on the netbook?

Usually, when I ran a dual boot machine, Ubuntu detected the other OS and asked me if I wanted to install Ubuntu along side that OS.  You should then be able to choose to use the existing free space for the Ubuntu install.

---

### Post by Mark Phelps on 2012-01-01
> **aditya_lugia said:**
> I am currently running Windows XP service pack 2.Its a netbook so it doesn't support windows 7.
Sorry to hear that.
> My hard disk has no partition( but it does free space upto 70GB).
Not possible.  Windows must have at least ONE partition in order to be installed and run. 
> The problem I am facing is that I do not know the procedure to create a new hard disk partition using Ubuntu installation.
The procedure, given you're using XP, is to boot from an Ubuntu CD, open Gnome Partition Editor (GParted), and use it to shrink the right-most Windows partition (in the display) to make room for Ubuntu.  But, if your Netbook has no CD drive, then you will need to read up on unetbootin (or use the Universal USB Installer from PendriveLinux.com) to create a bootable USB stick -- presuming your Netboot CAN boot from USB.
> I am unable to access the hard disk through Windows xp so please guide me in your procedure using Ubuntu only(P.S its mounted on pen drive).
Then, how do you know your hard disk is not DEAD?
To find out, once you get the bootable USB stick created for Ubuntu, boot from it, open a terminal and enter "sudo fdisk -lu (lowercase L, not a one).  That will list out the partitions on your drive so we can see what is there.
> I would be grateful if you could give me a step by step link to create a new partition on the empty space and install Ubuntu 11
If, as you say, there were NO partitions on your disk, it would ALL be empty space.  Need the results of the fdisk command before we can go any further.

---

