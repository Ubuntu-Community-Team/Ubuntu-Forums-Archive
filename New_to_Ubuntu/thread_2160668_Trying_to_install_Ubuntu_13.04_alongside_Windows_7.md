---
title: "Trying to install Ubuntu 13.04 alongside Windows 7"
date: 2013-07-07
forum: New to Ubuntu
---

### Post by xeredar on 2013-07-07
Hi Community,

first of all, I did a search on this forum and google for the Problem first, but I didn't found my exact problem or a fitting solution so I decided to ask the Pros :D

I always wanted to use Linux but never did because I have to use too many programs that run exclusively on windows. But curiosity won and so I installed Ubuntu on my netbook. I really love Ubunut but needed Windows, so i reinstalled Windows (8) on my netbook but installed Ubuntu alongside. Without any problems at all. Now i can select my preferred OS at startup and I really really love that setup.

I wanted to setup my Main Laptop the same way, which has currently Win7 64bit installed and I would like to keep it that way. I downloaded Ubuntu, created a bootable USB-Drive and started it. Everything went fine. I chose, install in Windows 7 and it rebooted. I wondered a bit, because it didn't do that as I tried to install Ubuntu with Win8 but whatever, it is a different OS even it is still Windows. Win7 started, an Ubuntu installer opened with some options which I left unchanged (I only set a PW) and it started to do its thing. But at the very end, an error message popped up and the whole installation got cancelled. Did I do something wrong in the process? Or do I have to do something else to prepare for the installation?

Please Ubu-Wan Community, you are my last hope!

Thanks in advance

Xeredar

---

### Post by Impavidus on 2013-07-07
> **xeredar said:**
> ...
I chose, [COLOR=#ff0000]**install in Windows 7**[/COLOR] and it rebooted. I wondered a bit, because it didn't do that as I tried to install Ubuntu with Win8 but whatever, it is a different OS even it is still Windows. [COLOR=#ff0000]**Win7 started, an Ubuntu installer opened**[/COLOR] with some options which I left unchanged (I only set a PW) and it started to do its thing. ...
Sounds like wubi, but as far as I know there is no official wubi of 13.04. Wubi doesn't like Win 8, but maybe that was a regular dual boot. Could you elaborate on that?

Also, MBR versus GPT partitioning could make an important difference. Can you check both your computers for that?

---

### Post by xeredar on 2013-07-07
You lost me at "Sounds like ..." ^^ I just downloaded the .iso from the ubuntu website and didn't install any other software for the purpose of installing other than the tool that allowed me to create a bootable USB. So i don't think it is WUBI unless said "thing" (means I have no clue what WUBI is) just installs itself or something.

To your second question: How do I check and more importantly what do i check? I never did more with partitions than to format them sometimes or reinstall windows on them. So I am a real noob in that regard and need further elaboration on that. What I can say is that all partitions are in the state i bought them (aside from the mentioned reinstalled OS)

---

### Post by waynefoutz on 2013-07-07
the process you're describing sounds like wubi, which is a windows installer. It doesn't create a partition, the install program runs in Windows. It creates a huge file, and treats it like a drive. This method hasn't been available since version 12.04, probably because it has issues with Windows 8.  Are you sure you're using 13.04 and not 12.04?

---

### Post by waynefoutz on 2013-07-07
the process you're describing sounds like wubi, which is a windows installer. It doesn't create a partition, the install program runs in Windows. It creates a huge file, and treats it like a drive. This method hasn't been available since version 12.04, probably because it has issues with Windows 8.  Are you sure you're using 13.04 and not 12.04? Either way, ignore what Windows says when you insert the disk or USB stick, reboot, then follow the prompts generated from he installation media.


sorry for the double post, bad editing on my part.

---

### Post by Penguenci on 2013-07-07
"Install in Windows 7" most definitely sounds like Wubi. What else could "install in Windows 7" mean? Unless your wording is off, I can assure you that you didn't attempt to "install Ubuntu alongside Windows" even if you meant to. It's more like installing Ubuntu as a separate application on Windows that acts as an operating system within itself. Just be a little more careful and make sure you're really installing it as a separate OS altogether. That should solve the problem and give you the exact same experience you got with your Netbook.

---

### Post by su:bhatta on 2013-07-07
yes, that definitely sounds like Wubi... but then again, with 13.04 that cannot be an option ! 

Also , check if the Bios is set-up to boot from USB stick, if you have that set up how can Windows7 boot up? At the first screen u should be able to boot from the Live USB n install Ubuntu 'alongside Windows7'....

---

### Post by xeredar on 2013-07-08
Okay guys, sorry for the wait but had to sleep :)

Here are the updates:

The Version I'm using is 13.04 unless the program is lying to me. ([http://imgur.com/5Y5fx9z](http://imgur.com/5Y5fx9z))

[IMG]http://imgur.com/5Y5fx9z[/IMG]

The Link (if the image should not work) is a screenshot of the program while it tries to install Ubuntu.

Evene though english is not my native language, the wording in my part was correct. When I installed Ubuntu with Win8, the option was called "Install ubuntu alongside Windows" but this time **inside** Windows, but since that is the only option despite removing windows and do some partitioning stuff that I do not understand and therefore do not want to mess with on my own without a clue, I chose that.

There is an option window before the screenshot i took (which I forgot to capture) which is plain grey with some drag down menus. The settings that i can set/choose (don't know which word is the right one :D) are the partition to install Ubuntu on, the Installation Space (don't know what that one means but I can allocate space from 4GB to 30GB from a drop down menu), user name, Ubuntu Version (Lubunut, Kubuntu etc.) and Password.

All my partitions are NTFS if anyone wants to now.

I used a total of two different bootable USB-creators and both times the same happened.

I didn't change anything in my BIOS. I can simply press F11 while my pc is starting up and get a "BIOS-looking" menu in which I can choose which drive should boot. There i choose the USB drive and get the option to either boot normal, check the "CD", try ubuntu without installing, install ubuntu and some others that i cannot recall right now. (All of those are before the USB stick tries to boot the ubuntu interface). I chose "Try Ubuntu without installing" to see if there are any errors and the GUI loads and I can play around like I could when I tried to install it with Win8). I setup my Wireless and click on "Install Ubuntu". Then I can choose, the language, if I want to install third party and updates (you know which one I mean) and after that I get the installation options that I mentioned above. There are also two options that are greyed out and are only available if I choose to remove Windows 7.

On the partitioning screen I get one "parent directory" and five smaller "partitions" (sorry if this gets confusing ... I don't know how to describe it in a better way) which have varius amounts of space, though I really only have two partitions: The main one (with windows on) and a recovery one (Which was precreated).

The one thing that could be (the Idea came while answering your replies) is, that Ubuntu tries to restart in Ubuntu (from the USB stick) but can't, because I did not set the USB stick as the first boot sector. On the other hand the Option within Ubuntu is so strangely named that I doubt this is the problem.

Thanks for all the replies btw! I really appreciate that!

---

### Post by Aparajita on 2013-07-08
[FONT=verdana]I think choosing "Install IN Windows 7" is where you went wrong. Like everyone else has been saying, that's a "thingy" (Wubi) that doesn't officially work anymore.

May be you should just re-insert the USB, and when it gives the boot options, post what all options you get?? Am sure someone here will be able to guide you exactly which option to choose. And you said you got an error. Do you have any idea what the error message said? I did a Wubi 10.04 install (that's just some Ubuntu install, never mind what) once and it kept giving me error messages. Ultimately choosing a different partition to load it on solved the problem, though only the Linux Geeks know why that happened.
[/FONT][FONT=verdana]
And @[**[COLOR=#000000]bhattabhishek[/COLOR]**]("http://ubuntuforums.org/member.php?u=1819052") 	 he says Windows started after the re-boot, so am assuming the first time it did boot from the USB Stick first time when he chose the "options". I think this must be a case of mistaken identity [/FONT]:( [FONT=verdana]He must be using some older version of Ubuntu, which did have a Wubi installer as part of the bundle.[/FONT]

---

### Post by xeredar on 2013-07-08
i think i answered your question with my recent post :)

---

### Post by fantab on 2013-07-08
Now, are you trying to dual boot with Windows8 or Windows7? Though you thread title says 7, i am a bit confused.

> All my partitions are NTFS if anyone wants to now

Before you install Ubutnu you need to create some 'unallocated space' using Windows tools ONLY. This can be done using 'Shrink' partition by right-clicking on the disk-partition in explorer. Ubuntu does NOT install on NTFS. When Ubuntu installer, Ubiquity, sees unallocated space it makes itself two partitions, one for '/' and another SWAP, if you choose auto install methods. If you need manual control then choose 'Something Else' Option. You can also create partitions for Ubuntu before hand using GPARTED that is present on Ubuntu install disk.

For Ubuntu you need partitions:
30GB Ext4 '/' (for Ubuntu system files and programs)
2-4GB SWAP 
??GB Ext4 '/home' (to house your personal Data)

Are you aware of the only 4 Primary Partitions limit on 'msdos' partition table?
Well, with 'msdos' parttition table you can only have FOUR Primary Partitions. To overcome this limitation we create the FOURTH Primary Partition as EXTENDED.
'Extended Partititon' is a Primary Partition and serves as a 'container' for LOGICAL Partitions. Within an Extended Partition we can have more than 100 Logical Partitions.
Ubuntu and most of the other Linux Distros can boot from Logical Partitions but Windows WON'T.

Post a screen shot of your HDD and its partitions from Windows Disk Management Tool.
Boot with Ubuntu LiveDVD/USB and "Try Ubuntu without installing". Let the desktop load. Open Terminal [Ctrl+Alt+T], run the following commands and post the output here:

```
sudo fdisk -l
sudo parted -l
```

Lastly from where did you download your Ubuntu.iso? Download it from [**here**]("http://www.ubuntu.com/download/desktop"), if you didn't.

---

### Post by xeredar on 2013-07-08
> [COLOR=#000000]Now, are you trying to dual boot with Windows8 or Windows7? Though you thread title says 7, i am a bit confused.[/COLOR]

Windows 7. Windows 8 is only used on my netbook and i refer to it this often because with my netbook there were absolutely no problems!

> [COLOR=#000000]Lastly from where did you download your Ubuntu.iso? Download it from [/COLOR][**here**]("http://www.ubuntu.com/download/desktop")[COLOR=#000000], if you didn't.[/COLOR]

Thats where I got mine.

> [COLOR=#000000]Before you install Ubutnu you need to create some 'unallocated space' using Windows tools ONLY. This can be done using 'Shrink' partition by right-clicking on the disk-partition in explorer. Ubuntu does NOT install on NTFS. When Ubuntu installer, Ubiquity, sees unallocated space it makes itself two partitions, one for '/' and another SWAP, if you choose auto install methods. If you need manual control then choose 'Something Else' Option. You can also create partitions for Ubuntu before hand using GPARTED that is present on Ubuntu install disk.[/COLOR]

[COLOR=#000000]For Ubuntu you need partitions:[/COLOR]
[COLOR=#000000]30GB Ext4 '/' (for Ubuntu system files and programs)[/COLOR]
[COLOR=#000000]2-4GB SWAP [/COLOR]
[COLOR=#000000]??GB Ext4 '/home' (to house your personal Data)[/COLOR]

Have really no experience with that. But will try to do it as you explained.

> [COLOR=#000000]Are you aware of the only 4 Primary Partitions limit on 'msdos' partition table?[/COLOR]
[COLOR=#000000]Well, with 'msdos' parttition table you can only have FOUR Primary Partitions. To overcome this limitation we create the FOURTH Primary Partition as EXTENDED.[/COLOR]
[COLOR=#000000]'Extended Partititon' is a Primary Partition and serves as a 'container' for LOGICAL Partitions. Within an Extended Partition we can have more than 100 Logical Partitions.[/COLOR]
[COLOR=#000000]Ubuntu and most of the other Linux Distros can boot from Logical Partitions but Windows WON'T.[/COLOR]

No I wasn't and still not sure if I am ^^ I only have my two Drives (C:/ and R:/) and thats all I know about that.

> [COLOR=#000000]Post a screen shot of your HDD and its partitions from Windows Disk Management Tool.[/COLOR]

[http://imgur.com/o8gS3Ds](http://imgur.com/o8gS3Ds)   <--- This one? Hope its no problem its in german. I will provide translations if necessary or can switch to english and take the screenshot again if you need it.

EDIT:

Here are the "pastes" from the console commands:

sudo fdisk -l gave me the follwing

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2bd2c32a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   890783743   445288448    7  HPFS/NTFS/exFAT
/dev/sda3       890783744   974669823    41943040    7  HPFS/NTFS/exFAT
/dev/sda4       974669824   976771119     1050648   12  Compaq diagnostics

Disk /dev/sdd: 31.4 GB, 31406948352 bytes
255 heads, 63 sectors/track, 3818 cylinders, total 61341696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048    61341695    30669824    c  W95 FAT32 (LBA)
```

for 

sudo parted -l I got

```
Model: ATA ST9500325AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  106MB  105MB   primary  ntfs         boot
 2      106MB   456GB  456GB   primary  ntfs
 3      456GB   499GB  42.9GB  primary  ntfs
 4      499GB   500GB  1076MB  primary  ntfs         diag


Model: Lexar USB Flash Drive (scsi)
Disk /dev/sdd: 31.4GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  31.4GB  31.4GB  primary  fat32        boot, lba
```

---

### Post by fantab on 2013-07-08
Ok... In the screenshot you can see that you have 4 partitions and a usb. Now,  those 4 partitions are PRIMARY. So if you force a fifth then your Partitions will turn from 'Basic' to 'Dynamic'. And Ubuntu won't install, read and write to 'Dynamic Partiion'.
(In future please use English when you post any information from your computer, it will be easy for us who don't know German and moreover this is an English Forum).

So, don't do anything right now. We need to see the output from the commands I posted in my earlier post.

---

### Post by xeredar on 2013-07-08
i edited my answer with the informations.

and sorry for the german screenshot, will remember it for the next time.

---

### Post by Dozy Van on 2013-07-08
EDIT: bad post please remove

---

### Post by fantab on 2013-07-08
Ok.. To install Ubuntu we need to delete one of your partitions, perferably the last D, which I think is a 'Recovery Partition' and/or has Compaq diagnostic tools.

But first we have to:
1. Create a Backup for your HDD after Shrinking the C partition to create space for Ubuntu. Are you comfortable with 100GB for Ubuntu?
Read here to learn how to Shrink:[ http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html]("http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html")
You will have 'Unallocated Space' now. Leave it alone. Don't do anything to that space.
After you have used Shrink. Reboot Windows a couple of times. Windows will run chdsk if need be to fix file-system errors, if any.
2. Copy all the contents of the 'D' partition to a separate folder on C or externally to a USB. You might need those tools later.
3. Download and install [Macrium Reflect]("http://www.macrium.com/reflectfree.aspx") (free version should do). Run it on Windows.
-- Make an Image of all the HDD to an external Disk or DVD. [More Info]("http://kb.macrium.com/KnowledgebaseArticle50074.aspx").
-- Create and burn a Linux Boot CD using Macrium Reflect: [More Info]("http://kb.macrium.com/KnowledgebaseArticle50047.aspx")
-- Connect the external disk on which you make the image of your Disk, boot from the Linux  Boot CD, start image [Restore]("http://kb.macrium.com/KnowledgebaseArticle50079.aspx") -- and make sure see the  saved images.  Do NOT do the actual restore. This is just to confirm that  your backup is good and can use it later if need be.

We are doing this because if we make any changes to the windows partitions then the Recovery may not work. Or If we delete the recovery partition then if there is a need to 'recover windows' we can safely restore the windows to the factory settings. This can also be use useful if and when you want to resell your machine.
We will delete D because its easier to do so. If you want to delete any other partition please do so but then you will have problems moving 'unallocated space' created after C partition.

4. Now delete the D partition and do this from Windows only using Windows Disk Management tool. and Reboot Windows. Shut down.

5. Boot with Ubuntu DVD/USB and either install it automatically using 'Install Alongside Windows' option... (I don't recommend this).

OR

5. Boot with Ubuntu DVD/USB, "Try Ubuntu without installing". From the desktop open GPARTED. [More Info]("http://www.dedoimedo.com/computers/gparted.html").
--Select the 'Unallocated space' that we have created earlier create an EXTENDED Partition. After creating an Extended Partition you will still see 'Unallocated space' equal to the size of Extended P. 
--Now from this 'Unallocated space' create three LOGICAL partitions as suggested earlier.
--From Desktop 'Install ubuntu'. At the dialog which says "Installation Type' choose 'Something Else' Option. This should open another dialog which shows your Partitions.
--Select the 30GB partition and hit 'Change' check format, Use As=Ext4, Mountpoint=/
--Select 2-4GB Partition, hit Change, Use As=SWAP or Linux Swap
--Select ??GB Partition, hit change, USe As=Ext4, Mountpoint=/home and check format. APPLY.

Continue with Installation.

If you don't want Backup of your Hard Disk Drive then ignore the steps 1-3

Good Luck...

---

### Post by xeredar on 2013-07-08
Okay, the saving part took quite a bit of time and I'm now at the step of creating the USB-Stick (Step 3.2) but in the tutorial they say that i have to format the stick to FAT16, which means that i can only use an usb stick with 4GB or less which I do not have. I have only 8GB and 32GB. Is it really necessary for this to work that it is FAT16, or can I use FAT32 instead?

---

### Post by bcbc on 2013-07-08
Just FYI for anyone... Ubuntu will still offer to install *inside* windows (i.e. with Wubi) if it finds all primary partitions used. (Despite claims that Wubi is not supported in 13.04, ubiquity has a built-in check and if it finds wubi.exe on the CD, it will give this option). So you may get this option even when installing from the DVD/USB. 

See here for details: [http://askubuntu.com/a/272036/14916](http://askubuntu.com/a/272036/14916)

[IMG]http://i.stack.imgur.com/WSbMV.png[/IMG]

---

### Post by fantab on 2013-07-08
> **xeredar said:**
> Okay, the saving part took quite a bit of time and I'm now at the step of creating the USB-Stick (Step 3.2) but in the tutorial they say that i have to format the stick to FAT16, which means that i can only use an usb stick with 4GB or less which I do not have. I have only 8GB and 32GB. Is it really necessary for this to work that it is FAT16, or can I use FAT32 instead?

I'd say use DVD as it will be permanent. You might need USB sooner than you think. OR have a .iso image safe and then use USB. Try FAT32 it should work. (I haven't tried this on USB).

@ bcbc: Thanks for the info.

---

### Post by xeredar on 2013-07-09
tried FAT32, worked just fine. Thanks everybody for your help! :D

---

