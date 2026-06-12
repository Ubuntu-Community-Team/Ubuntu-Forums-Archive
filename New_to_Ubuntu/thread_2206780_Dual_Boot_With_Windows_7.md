---
title: "Dual Boot With Windows 7"
date: 2014-02-20
forum: New to Ubuntu
---

### Post by Joe_Ciaravino on 2014-02-20
I have installed Windows 7 onto the entire primary SSD on my desktop, and then tried to install Ubuntu 12.04.2 by using a bootable Ubuntu ISO CD. I get through much of the install program, and get 2 choices and choose "Something Else". I chop off 30 Gb from the Win 7 partition and now have it as "unallocated space". I then attempt to install Ubuntu to the 30 Gb unallocated space, but am unable to do so. Must I further subdivide/partition this space for a successful install?
Thanks in advance.

---

### Post by cy1on on 2014-02-20
Hmm. Have you tried installing this way: [http://www.ubuntu.com/download/desktop/install-desktop-latest](http://www.ubuntu.com/download/desktop/install-desktop-latest) ? (The easiest way)

---

### Post by Joe_Ciaravino on 2014-02-20
I try to install UBUNTU 12.04.3 and get a menu saying "there is no other  o.s. installed on this drive, what would you like to do:

1. Install UBUNTU
2. Something else.

I do not get the choice to  "Install beside Windows 7".

What do I do????? Help!!!

---

### Post by cy1on on 2014-02-20
Try installing 13.10 instead and see what results you're getting. It's more up to date.

---

### Post by Joe_Ciaravino on 2014-02-20
There appears an "EFI System Partition" in Disc Manager as well.

---

### Post by oldfred on 2014-02-20
Is this a new system?
Post this from live installer terminal

sudo parted -l

Generally better to use Windows tools to shrink Windows and immediately reboot so it can run its chkdsk. It need chkdsk after any resize.
Also Ubuntu will not see NTFS partitions that are hibernated or need chkdsk, so make sure to turn off hibernation.

---

### Post by amber4 on 2014-02-20
I had the same issue with Windows 8 (not recognizing Windows as being installed as another OS), and I ended up manually partitioning the disk, creating a swap space and installing on the new (not swap) partition. Here's a tutorial: [link] [http://www.youtube.com/watch?v=wNCSbTyUzoM](http://www.youtube.com/watch?v=wNCSbTyUzoM) [/link] It's what I used to help me partition the disk and get Ubuntu on without wrecking Windows. Even though we all know Windows is.. well, I won't start. ;) Even though it's for Windows 8, the Disk Management tool works the same in both Windows 7 and 8 and you should be able to get the extra space for the partition pretty easily. :) Then just follow the instructions for creating the swap partition (about 10% of the partition you created and formatted according to the video) and you should be dual-booting Windows and Ubuntu fairly quickly. :)

EDIT: Correctly formatting the newly created partition to ext4 is included in the tutorial, so you wouldn't be trying to install into any unallocated space.

---

### Post by JeQhdMD on 2014-02-21
Joe,

Your win7 install may be damaged as you did not use the native Win7 apps to defrag, and then the windows partition program to shrink windows.  Often, it can only be reduced by 50% of the drive capacity (e.g., 500gb to 250gb or about).   Additionally, immediately after resize, a reboot back into Win7 was required so windows could recertify (verify) disk integrity.

Once Win 7 did a "normal" restart (2nd reboot), then you could load the Linux live CD or flash stick to initiate the Linux install.   Further, you can't install Linux into "unallocated" disk space without use of a tool like gparted to assign a "file-system" to the unallocated space.  Ext4 is probably the best choice for new linux users.   The unallocated space could also be split further into additional logical partitions , as long as each is assigned a linux file system (or a neutral file system like FAT32 for data files only).

Because you indicated your system is not using traditional BIOS - - you should read up on dual booting for UEFI systems.   It takes more planning and work sometimes (as the hardware vendors do not always implement UEFI in a consistent way across various hardware.  Especially, read all of Old Fred's links, and read the official Ubuntu documentation for the full instructions and alternatives.

---

### Post by amber4 on 2014-02-21
Sorry, my last post was extremely unclear and sales pitch-y. :P Woops.

What you could do is go into win7, control panel and search for disk management. Then you right-click the partition you want to shrink (I chose C: ) and click "Shrink Volume." Then you have a bunch of unallocated space. This will become your Ubuntu partition.

After shrinking your win7 partition, boot back into Windows. Reboot again, this time loading the live CD and start the install. When asked to 1.install Ubuntu or 2.Something else then choose Something else. You can then click on the free space, click the "+" in the lower-ish left hand corner and create a swap space by changing the size to about 10% of the space you freed up. Leave the partition type as Logical and at the beginning of the space. Then click the drop-down menu "Use as:" and select "swap area." Remember, this should be with the size chosen as 10% of the space you want Ubuntu to run on. Hit OK, and notice the swap area listed under /dev/sda as swap.

You then want to select the remaining free space, hit "+" again. Leave the size alone. Select the partition type as "primary" and leave it at the beginning of the space. Under "use as" it should be "ext4 file journaling system." Set the mount point to "/" so it mounts at root. Hit OK, select the new ext4 partition and continue with the install.

---

### Post by IvoGuerreiro on 2014-02-21
I hope my last experience helps.:P


I recently i choose to install ubuntu on my laptop hard drive.
I just have one SSD, so i created a partition, and i formated it.


After, i mounted a drive in daemon tool to install ubuntu, he dont asked me if i wont to install beside Windows 7, because in that partition you dont have anything, so he can not detect other OS. (in my situation, i just keep going forward).


I have installed successfully Ubuntu 13.10.


now when i start my laptop it detects 2 OS (one on each partition so, he always ask me which one i want to start. 


if i dont choose after 10 second or something like that he just start W7.

sorry about any misspelling, it's not my native language, any way.
i hope i have written in a perceptible way.

---

### Post by Joe_Ciaravino on 2014-02-24
> **amber4 said:**
> Sorry, my last post was extremely unclear and sales pitch-y. :P Woops.

What you could do is go into win7, control panel and search for disk management. Then you right-click the partition you want to shrink (I chose C: ) and click "Shrink Volume." Then you have a bunch of unallocated space. This will become your Ubuntu partition.

After shrinking your win7 partition, boot back into Windows. Reboot again, this time loading the live CD and start the install. When asked to 1.install Ubuntu or 2.Something else then choose Something else. You can then click on the free space, click the "+" in the lower-ish left hand corner and create a swap space by changing the size to about 10% of the space you freed up. Leave the partition type as Logical and at the beginning of the space. Then click the drop-down menu "Use as:" and select "swap area." Remember, this should be with the size chosen as 10% of the space you want Ubuntu to run on. Hit OK, and notice the swap area listed under /dev/sda as swap.

You then want to select the remaining free space, hit "+" again. Leave the size alone. Select the partition type as "primary" and leave it at the beginning of the space. Under "use as" it should be "ext4 file journaling system." Set the mount point to "/" so it mounts at root. Hit OK, select the new ext4 partition and continue with the install.

This method allowed me to install Ubuntu. I then did a cold boot, but got no choice menu. It immediately booted to Win7. 

Your instructions were easy to understand, and I haven't tried any of the other suggestions yet.

I have a nauseating feeling that without the third choice ("Install Ubuntu along side windows") that I won't be able to do this. 

It is a SSD. Does that explain the 100 mb "healthy" system partition" with no drive letter that appears before C drive? Is it possible that this is the culprit?

When I installed windows 7, it was a clean, normal installation, as far as I know.

---

### Post by Mark Phelps on 2014-02-24
> It is a SSD. Does that explain the 100 mb "healthy" system partition" with no drive letter that appears before C drive? Is it possible that this is the culprit?That small partition is the new "boot" partition containing the Windows boot loader files.  If you trash it in any way, Windows will no longer boot.  The fact that it is on an SSD instead of an HDD makes no difference.

> When I installed windows 7, it was a clean, normal installation, as far as I know. When you install Win7 to a blank drive, the installer automatically creates the 100MB "boot" partition without telling you.  It does that to permit encryption of the Win7 OS partition.

If you aren't encrypting your Win7 OS partition, you don't need to have the boot loader in its own partition.  To move it to your Win7 partition, do the following:
1) Download and install EasyBCD from NeoSmart Technologies
2) Run EasyBCD and select the following: BCD Backup/Repair --> Change boot drive.

That will migrate the boot loader files to the partition you select.  After that, you no longer need the "boot" partition and can remove it.

---

### Post by Joe_Ciaravino on 2014-02-24
> **Mark Phelps said:**
> That small partition is the new "boot" partition containing the Windows boot loader files.  If you trash it in any way, Windows will no longer boot.  The fact that it is on an SSD instead of an HDD makes no difference.

When you install Win7 to a blank drive, the installer automatically creates the 100MB "boot" partition without telling you.  It does that to permit encryption of the Win7 OS partition.

If you aren't encrypting your Win7 OS partition, you don't need to have the boot loader in its own partition.  To move it to your Win7 partition, do the following:
1) Download and install EasyBCD from NeoSmart Technologies
2) Run EasyBCD and select the following: BCD Backup/Repair --> Change boot drive.

That will migrate the boot loader files to the partition you select.  After that, you no longer need the "boot" partition and can remove it.

Did as you suggested but no-go......the easy BCD won't let me do it.
Drive "C" is already listed as the primary/boot/system partition.
The unidentified 100mb partition is not shown as the boot partition. It is totally unlabeled. If I left click on it in "windows disc management" utility, all options are grayed-out.

I would love to have UBUNTU, but it seems unlikely. I don't want to damage the Win7 installation, as I have over 24 tweaking hours invested in it already!!!!!

Any help would be much appreciated!!!

---

### Post by oldfred on 2014-02-24
Best then to see all the details. And we normally suggest a full backup of Windows before major changes like a another operating system.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Boot-Repair can only do minor fixes to Windows. If Windows repairs are required you need a Windows repairCD or Flash drive.

---

### Post by Mark Phelps on 2014-02-24
> I don't want to damage the Win7 installation, as I have over 24 tweaking hours invested in it already!!!!!

Hey, I understand ... really!!

So, do yourself a favor and do two things BEFORE you start messing around with dual-booting:
1) Use the Win7 Backup feature to create and burn a Win7 Repair CD.  This will provide you the tools needed to repair or restore Win7 boot capability -- should anything happen to it during your dual-boot setup.
2) Download and install the free version of Macrium Reflect in Win7.  Then, connect an external drive and do a full image backup to the external drive.  When running MR, click on the Backup tab, then choose the option "Create an image of the partition(s) required to backup and restore Windows".  Once that is done, use Other Tasks to Create Rescue Media -- and create the Linux Boot CD.  NOW, you have the capability of completely restoring a working version of Win7 in just a few minutes.

---

### Post by Joe_Ciaravino on 2014-03-04
> **cy1on said:**
> Try installing 13.10 instead and see what results you're getting. It's more up to date.

No difference.....it doesn't see that Windows is installed.....it sees no other OS installed

---

### Post by Joe_Ciaravino on 2014-03-04
> **oldfred said:**
> Best then to see all the details. And we normally suggest a full backup of Windows before major changes like a another operating system.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Boot-Repair can only do minor fixes to Windows. If Windows repairs are required you need a Windows repairCD or Flash drive.


THIS IS WHAT I HAVE TO DO AND APPRECIATE ANY HELP.
I write the commands as shown on the page, from a terminal. But when I type boot-repair it shows as invalid command. then go to the "dash" but get nothing

this is sooooo frustrating

I don't want to try any repairs myself.

I only want to do this, so that a report will be generated and YOU will see what the problem is.

Please help me generate a "boot report" that you can evaluate and recommend how to fix.

I have a feeling that I'm typing something incorrectly.
Is that ONE or TWO separate commands that need to be typed in the "terminal"??
Please give me some idiot proof instructions.
Thank you!

---

### Post by oldfred on 2014-03-04
You can copy  & paste commands into the terminal. That often avoids typos and even spaces which may not always be clear that they are a space are important.  Also in Linux case matters, so no caps unless required.
You also have to have working Internet as it is downloading the boot-repair app.

sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

The && are to combine two lines into one. The second line then also launches boot-repair.
If you are using liveDVD or flash drive you have to reinstall each time you reboot.

---

### Post by Joe_Ciaravino on 2014-03-04
> **oldfred said:**
> You can copy  & paste commands into the terminal. That often avoids typos and even spaces which may not always be clear that they are a space are important.  Also in Linux case matters, so no caps unless required.
You also have to have working Internet as it is downloading the boot-repair app.

sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

The && are to combine two lines into one. The second line then also launches boot-repair.
If you are using liveDVD or flash drive you have to reinstall each time you reboot.

OK......was able to burn ISO to CD:

here's the URL of my boot info:

[http://paste.ubuntu.com/7035141/](http://paste.ubuntu.com/7035141/)

---

### Post by oldfred on 2014-03-04
You have a Windows UEFI install.
Somehow you have grub2 install to the MBR of the 256GB drive for a BIOS boot, but no Linux install.
You also show sdb in MBR(msdos) format.

Are you trying to install Ubuntu in sda (256GB SSD) or the 1TB hard drive.
Since hard drive is MBR, you can only install in BIOS boot mode, and if it wants to install grub to sda, it will not install correctly unless you have a 1MB unformatted partition with the bios_grub flag.

But better to have both drives as gpt and both installs as UEFI.
If you also want Ubuntu on 256GB drive, use need to use Windows to shrink the Windows NTFS partition and reboot so it can adjust to its new size and run chkdsk. Do not hibernate. 
Then you should be able to install Ubuntu into unallocated space.
How you boot install media is how it installs, so you want to boot Ubuntu in UEFI mode.

 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

More info in Link in my signature.

---

### Post by Joe_Ciaravino on 2014-03-04
Please just recommend something to do. Make it simple.
Should I simply follow the recommendations at the bottom of the boot repair printout?

---

### Post by oldfred on 2014-03-04
You only have Windows installed.
What is it you want to do?

---

### Post by Joe_Ciaravino on 2014-03-04
> **oldfred said:**
> You only have Windows installed.
What is it you want to do?

I want to fix the hard drive (if necessary) in order to install ubuntu, dual boot with windows 7. Should I simply follow the recomendatios at the bottom of the repair disc printout?

---

### Post by oldfred on 2014-03-04
See posts #8 & 22. Boot-Repair will not install Ubuntu.

You should be able to go into UEFI/BIOS and choose Windows if you want to boot Windows.
Boot-Repair can only do minor fixes to Windows, so if you have other issues with Windows you need a Windows repair flash drive.

---

### Post by Joe_Ciaravino on 2014-03-07
If I run Boot Repair and ask it to repair rather than generate a report, will I be able to install Ubuntu.

---

### Post by oldfred on 2014-03-07
Not sure there is much Boot-Repair can do for a UEFI Windows install. It should boot from UEFI anyway and if not then you need your Windows repair flash drive.

---

### Post by amith3 on 2014-03-11
what error message you got when trying to install on the 30gb unallocated space ?

---

### Post by Joe_Ciaravino on 2014-03-11
> **amith3 said:**
> what error message you got when trying to install on the 30gb unallocated space ?

No error message. It installs perfectly, only that when I boot my computer it boots into windows. I don't get a menu giving me a choice or which os to boot to.

---

### Post by oldfred on 2014-03-11
If your system is UEFI, you have to go into UEFI and choose what system you want to boot. And set Ubuntu as default boot if that is what you want.

With BIOS and still booting Windows, grub was not correctly installed and easiest to run Boot-Repair.

If still not working post new link to BootInfo report.
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by amith3 on 2014-03-11
download boot repair disc from the following link. run it like a live cd. 
[http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)

---

