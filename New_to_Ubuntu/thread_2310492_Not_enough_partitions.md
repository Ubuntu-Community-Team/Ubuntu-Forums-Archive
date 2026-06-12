---
title: "Not enough partitions"
date: 2016-01-19
forum: New to Ubuntu
---

### Post by gilly2 on 2016-01-19
Hi I'd really appreciate it if anyone could answer soon. Thanks in advance haha.
Anyway I'm new to ubuntu and I'm trying to dual boot on a windows pc. I made some free space on the hard drive and I went to install linux from a live usb. It did not give me the option to install alongside windows, but just to delete everything or "something else" I used a tutorial and went to something else. I made a partition for / and for /home, but now the empty space is unusable so I can't make a swap space partition. I think it is because I already have 4 partitions maybe? There were 2 on there already but why? Any help would be great. Thanks.

---

### Post by oldfred on 2016-01-19
Most Windows 7 systems used all 4 primary partitions. Windows has the Boot & main install , and vendor has recovery and a tools or utilities partition. I think they intentionally configure all 4 to make it difficult.

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by grahammechanical on 2016-01-19
Like my machine your computer has MBR partitioning. We are only allowed 4 primary partitions. For years the work around has been to use one of the 4 primary partition allocation as a special primary partition called an Extended partition. Inside that Extended partition we can create a very large number of Logical partitions.

If your 4 primary partition allocation is already used up, how did you create 2 new partitions? It should not be possible.

The usual procedure in the situation where the 4 primary partition allocation is already used up is to 

a) Delete one of the existing primary partitions. 
b) Create unallocated space by resizing one or two or all three of the remaining primary partitions. 
c) Create an Extended partition out of all the unallocated space
d) In the Extended partition create a logical partition (Ext4) for Ubuntu and another logical partition for swap.

If we want we can also create a logical partition for /home. If that is our desire.

If, in your case, there were only 2 primary partitions, then You could have used one of the remaining primary partition allocation for Ubuntu and the last of the remaining primary partition allocation as an Extended partition into which you create a logical partition for /home and a logical partition for swap.

Or put all 3 Linux/Ubuntu partitions as logical partitions inside the Extended partition. And so have one primary partition allocation left over.

Regards.

---

### Post by gilly2 on 2016-01-19
I forgot to mention that I'm using Windows 10 on a computer that I built myself. Do the windows 7 guides still apply?

Also Windows used to be taking up the whole drive but I shrunk it down to have the free space

Thanks oldfred but I still don't understand what to do. I'm pretty much a complete noob haha. I don't really want to mess around deleting stuff off of windows. Is there any other way? Perhaps easier or less dangerous?

---

### Post by verymadpip on 2016-01-20
Hi there.
Have a look in Windows 10 disk management to see your partition layout, or gparted from an Ubuntu live environment.
I've just looked at mine & all 4 primary partitions have been used.  I'm running Windows 8.1 which I installed myself upgraded to 10.
I have the partitions I expected to see: System Reserved, my C drive, a data partition for personal stuff, photos, movies, etc (D) & an unexpected (to me anyway) recovery partition of 450Mb...???!?


For me options would be:
1. Stick a new hard drive in there.
2. Delete a partition & create an extended one as grahammechanical has mentioned.
*Good to see you're being careful about this possible option by the way.*

I have a couple of old hard drives kicking about so I'd probably go with option 1.  I'm working on a desktop PC which makes that kind of thing a little easier than doing so on a laptop for example.

If I didn't want to throw new hardware in or didn't have a spare HDD  I'd probably back up all my personal stuff, delete what I refer to as my Data Partition & make that an extended for my ubuntu install.  This in itself could cause issues for me as I often install downloaded software to my data partition to keep space on the System/OS partition.

---

### Post by mastablasta on 2016-01-20
> **gilly2 said:**
> Thanks oldfred but I still don't understand what to do. I'm pretty much a complete noob haha. I don't really want to mess around deleting stuff off of windows. Is there any other way? Perhaps easier or less dangerous?

you can modify the primary partition into secondary using minitool partition wizard without the loss of data. however, as always when doing major changes to OS or partitions it is good to have a backup. easiest backup ti to image the whole disk for example using RedoBackup. or you can backup just the data.

the tool worked well in my case and I did not need any data restore. I just changed one partition into secondary, so I could create / and /swap in the free space.

---

### Post by oldfred on 2016-01-20
If you installed Windows 10 yourself, on a new system, did you install in the 35 year old BIOS/MBR configuration or the new UEFI/gpt configuration. Pre-installed systems since Windows 8 first came out use UEFI/gpt, but users can install either way. New systems offer to boot install media in either UEFI or BIOS mode and how you boot install media is then how it installs.

If you do not understand some of the terms, I do have definitions at end of the how-to thread linking in my signature.

You can also use fixparts to change a primary partition to logical. Perhaps not quite as easy as the MiniTool, but available in Linux. But do not convert a drive from MBR to gpt or vice-versa with Fixparts as Windows installed in one mode must keep same partitioning.
       [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
    
From Ubuntu live installer in terminal mode, post this to see partitions:
sudo parted -l

---

### Post by gilly2 on 2016-01-20
I have BIOS I'm pretty sure but I ended up installing ubuntu in logical partitions which apparently you're allowed to have more of.
I shouldn't have BIOS?

---

### Post by Geoffrey_Arndt on 2016-01-20
No Gilly2, you're not quite understanding.   Traditional BIOS (using disk partitioning protocol called Master Boot Record (aka MBR)) started to become obsolete in about 2010 - - by 2012 no new Win 8x came with it anymore.   The replacement is UEFI (Unified Extensible Firmware Interface).   What OldFred is saying is . . . since you installed the OS yourself, you had the choice of installing in the legacy (aka "Old") BIOS or the new UEFI.   IF you have UEFI, the limitation on number of partitions no longer applies (you can have hundreds if you choose).

To verify if running UEFI, you can run MSINFO32, click on System Summary and note the BIOS Mode field output.

So, if you did install using BIOS partitioning, yes, installing Ubuntu in Logical partitions is OK.   Need just two partitions - 1 for Ubuntu OS including home directory, and 1 for swap.   Some users prefer another separate partition for /home also, but is not needed (or recommended for 1st install).   Either before the install process, or during the install process, the Ubuntu partition need to be formatted with a Linux file system (ext4 is common).   Swap doesn't need formatting per-se.

---

### Post by oldfred on 2016-01-20
If both Windows & Ubuntu are installed in BIOS/MBR that is ok. 
It just is some minor advantages to newer UEFI/gpt configurations, but early on UEFI/gpt was not well understood and most suggested BIOS based installs.
Since Windows only boots from MBR with BIOS or only boots from gpt with UEFI, it can be a big change to convert. Usually best not to change.

---

### Post by oldfred on 2016-01-20
If both Windows & Ubuntu are installed in BIOS/MBR that is ok. 
It just is some minor advantages to newer UEFI/gpt configurations, but early on UEFI/gpt was not well understood and most suggested BIOS based installs.
Since Windows only boots from MBR with BIOS or only boots from gpt with UEFI, it can be a big change to convert. Usually best not to change.

---

### Post by gilly2 on 2016-01-21
I built the computer this year, well actually last year (towards the end of 2015). It's very new. I don't remember it asking me about BIOS or UEFI though. Ubuntu is working fine for me now so it's okay. The only problem now is that my ctrl, alt, and windows key are all being read as shift. I have a Redragon Karura and I heard the problem is common with other types of keyboards. Do you know how to fix it? Thanks for all of your help.

---

### Post by oldfred on 2016-01-21
On keyboard issue best to post new thread with that in title. Perhaps someone knows.

The only place you see UEFI or BIOS is during boot of flash drive installer. And how you boot install media, it then how it installs.

---

### Post by gilly2 on 2016-01-21
I installed from a cd that I bought online

---

### Post by oldfred on 2016-01-22
Ubuntu does not have CD, must have really been a DVD.
But you just download the ISO and install to either a DVD or flash drive for free. I prefer flash drives as they are reusable and you then can copy the newer version of Ubuntu when it comes out to same flash drive.

 Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it 
[http://ubuntuforums.org/showthread.php?t=2230389](http://ubuntuforums.org/showthread.php?t=2230389)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Lots more install info and many links in link in my signature, if you want UEFI.

---

### Post by gilly2 on 2016-01-22
I meant I installed windows with a disk. If its not necessary I don't want to get the UEFI. Is it?

---

### Post by oldfred on 2016-01-22
You should know how to get into UEFI/BIOS on your system, often f2 or del keys.
And generally some settings have to be changed especially with the new UEFI systems. Even if just to say to default to the CSM/BIOS/Legacy boot mode, not UEFI or UEFI with secure boot.

---

