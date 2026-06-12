---
title: "Questions on reworking my Dual boot."
date: 2014-09-20
forum: New to Ubuntu
---

### Post by kira-yamato-2008 on 2014-09-20
I have a couple of questions regarding reworking my own dual boot situation. 

The situation as it stands is this: I started with Lubuntu 14.04 and installed Ubuntu 14.04 along side it. I installed proprietary Nvidia binary drivers on Ubuntu and now it freezes about 30 seconds to a minute after boot, but since the Nvidia drivers don't work on it either I don't have much need for it.
 
What I want to do: Eliminate Ubuntu 14.04 and put Windows Vista on the Ubuntu (not Lubuntu) partition. 

My questions: Can I format the Ubuntu partition with out touching Lubuntu's own partition and install Vista on it without risking the data on the Lubuntu Partition? Also is there a way to keep the GRUB partition/OS manager so I can maintain access to both operating systems easily?  

I realize this question has probably been asked before, but I just can't seem to find the answers to my particular concerns.

---

### Post by JeQhdMD on 2014-09-20
If you have decent hardware, why not install Vista using Oracle's Virtual Box? . .  . . That way, you can keep Linux as the stable, goto OS, and _only use windows if absolutely needed_.

---

### Post by kira-yamato-2008 on 2014-09-20
Well the general idea is to use Windows only for things that only it can do. To be precise, 3D games. As I have an issue with Linux, current Nvidia binary drivers, and my aging GeForce 8200M G. While the card is still adequate for the things I want to run, and I know someone with the same machine running the current drivers on Windows Vista... Linux's compatibility with Nvidia drivers and this particular card just plain suck.

Due in part to those limitations Oracle's Virtual Box and the, in my humble opinion, far superior, VMWare Player won't allow my card to render, because I can only use the X.Org X Server Nouveau display driver. Also at least one of the games I played on a regular basis and want to play again... Detects virtual machines and doesn't allow them. But the larger issue is no 3D rendering in virtual machines for me anyways due to poor support for my card.

So I need to run Windows in dual boot just to utilize my graphics card. The Nouveau drivers are adequate for everything else aside from gaming applications.

Edit: *I want to avoid at this point having to do a full wipe and fresh install because I don't currently have an external hard drive with enough space to back up all my stuff to. I won't be able to afford one for at least a couple months at any rate. So I'd like a solution to keep my data, eliminate the second installed OS (Ubuntu) and keep the primary OS(Lubuntu) and it's partition fully intact.*

---

### Post by Rob Sayer on 2014-09-21
I'm no expert on nvidia drivers at all but try this:

[https://devtalk.nvidia.com/default/topic/675613/8200-igp-which-driver-version-/](https://devtalk.nvidia.com/default/topic/675613/8200-igp-which-driver-version-/)

---

### Post by kira-yamato-2008 on 2014-09-21
> **Rob Sayer said:**
> I'm no expert on nvidia drivers at all but try this:

[https://devtalk.nvidia.com/default/topic/675613/8200-igp-which-driver-version-/](https://devtalk.nvidia.com/default/topic/675613/8200-igp-which-driver-version-/)

Unfortunately due to support issues from Nvidia, which is notoriously bad with Linux, plus the older card... It just causes freezing for me... That said I really don't use things that tax the video card in Lubuntu. Since it's an older machine anyways I'd rather use a straight dual boot than virtual machines anyways, in case I hadn't made that clear enough.

What I'm looking for specifically is a way to keep the manager that I got when I installed Ubuntu alongside Lubuntu, when I install Windows Vista, and optimally do it all with out having to reinstall Lubuntu. Because I currently don't have the space to back up everything I have right now. Plus I'd like to if possible avoid reinstalling everything on Lubuntu.

---

### Post by oldfred on 2014-09-21
I have a slightly newer nVidia card 9600GT and have not had any issues as long as I install the driver from the repository thru system, software, drivers.

Systems seem to know if you have backed up or not. If you have good backups, your modifications will work without any issues. But if you have not backed up, your changes corrupt system and you lose lots of data or have to spend weeks with photorec trying to recover some data. Better to purchase drive, flash drive or DVDs and backup whatever is important.

Make sure your Lubuntu is reinstalled to the MBR. Since you install Ubuntu last it installed its copy of grub to MBR and you are booting thru it. You should just be able to boot into Lubuntu and install its grub to the MBR. Reboot to make sure that works before deleting the Ubuntu partition.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

You will have to have a primary NTFS formatted partition with the boot flag to install Windows. Normally Windows 7 wants two primary partitions, a 100MB boot & main install. But the 100MB boot is primarily in case you want to encrypt the main install. You can just install to one primary partition with all its boot files in that one NTFS partition.

Windows will overwrite the MBR and you have to restore grub. Easiest with Boot-Repair, but not difficult to just mount the partition and do a grub install from the Lubuntu live installer. Just be sure to have a working current version live installer handy.

      
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by kira-yamato-2008 on 2014-09-21
Thank you for the info oldfred. When I talk about back up it's just lots of user files I don't want to have to hunt down again. Mostly things like saved videos, pictures, music, PDF manuals, and documents.

It seems I have my options now. Follow the circle of installing Windows after Linux, which doesn't seem difficult, just a bit round about. On the other hand since a recent string of updates, and program removal(Bunch of software center games I never played anyways.) Lubuntu has slowed down some, so a complete reformat and reinstall looks slightly more attractive in the long run. I just need the external storage space to pull it off.

Anyways thank you again.

---

