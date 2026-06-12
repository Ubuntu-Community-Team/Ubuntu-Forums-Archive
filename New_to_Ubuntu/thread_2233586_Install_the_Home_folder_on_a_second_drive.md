---
title: "Install the Home folder on a second drive"
date: 2014-07-09
forum: New to Ubuntu
---

### Post by chris-burmajster on 2014-07-09
Hello Everybody,

In the next few weeks I'll be buying a new computer. It comes with a 120Gb SSD and a 2Tb conventional hard drive. When I install 14.04 I would like to have to have the Home folder on the 2Tb drive, so that I have more space for my data. How would I go about it?

Many thanks to you all.

Chris

---

### Post by sudodus on 2014-07-09
Create the partition for home, and when installing, select ***Something else*** at the partitioning page.

Select your home partition and assign it to be **/home** similar to how select and assign the root partition **/**

Then the installer will get it right.

It might also be a good idea to have a separate data partition, where you put your data files, for example documents, pictures, music files and video clips. Then it will be easy to backup those files independantly of the operating system (the root partition and the home partition).

I use such a data partition.

---

### Post by chris-burmajster on 2014-07-09
Hi Sudodus,

Thanks for your reply. I was under the impression that all your data files, documents, pictures etc live in the Home folder. That's exactly what I want to put on the 2nd hard drive. How do I tell the installer that? It only appears to see one hard drive.

Thanks,

Chris

---

### Post by yancek on 2014-07-09
>  I was under the impression that all your data files, documents, pictures etc live in the Home folder

No.  I imagine a lot of people do that but it certainly isn't necessaary.  Personally, I just use a / partition with the /home directory on it and then create a separate partition on which to put that type of personal data.  You can use the /home on a separate partition but it is a personal choice. 

If it is not seeing the second larger hard drive then you obviously won't be able to do it during the install.  Are you sure it is attached securely?  Are you using the 'Something Else' option suggested above?  You should then see all your drives/partitions in the main window of the 'Installation Type', scroll down.

---

### Post by sudodus on 2014-07-09
> **yancek said:**
> No.  I imagine a lot of people do that but it certainly isn't necessaary.  Personally, I just use a / partition with the /home directory on it and then create a separate partition on which to put that type of personal data.  You can use the /home on a separate partition but it is a personal choice. 

If it is not seeing the second larger hard drive then you obviously won't be able to do it during the install.  Are you sure it is attached securely?  Are you using the 'Something Else' option suggested above?  You should then see all your drives/partitions in the main window of the 'Installation Type', scroll down.

+1

---

### Post by oldfred on 2014-07-09
You cannot set up the data partition during the install. So after you boot new install you have to create a new data partition on hard drive and auto mount it by adding settings into fstab. And you have to set ownership & permissions to use it. So while I prefer the data partition, it is a bit more complicated to set up than just a /home in another partition which you can do during install.

Some info on all the added steps:

 I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

   The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

### Post by buzzingrobot on 2014-07-09
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving).

Lots of detail and a focus on precaution there.

---

### Post by chris-burmajster on 2014-07-10
Thank you all for your replies. 

As I haven't yet got the new computer, I can't answer the details; I just wanted to know what to do before it arrives, so that it goes smoothly when it does arrive. As I have about 30,000 photos, I can't put the Home folder on the tiny 120Gb drive, it has to go on the larger 2Tb drive, hence my original question. I thought that it might be easier to do during initial install, rather than let the installer do everything automatically and then change things around. 

At present, I plan to run GParted first, to format both drives as ext4, then run the installer. When I choose the 'something else' option, will I be able to allocate certain partitions to each physical drive? I want to have everything ***except*** the Home folder on the 120Gb drive and the Home folder on the 2Tb drive. Will the installer allow me to do that?

Chris

---

### Post by sudodus on 2014-07-10
You can put the Home folder (inside the root partition) on the tiny 120Gb drive, if you keep your 30,000 photos in a ***data*** partition in another drive. But your idea with a home partition in another drive is also good.

Yes, you can create partitions with ***gparted*** wherever you want them, and then select them in the installer at the 'something else' window.

If you want the root partition on the SSD and the home partition on the HDD, that is fine. You must also decide where to put the swap partition. It will be faster on the SSD, but will wear it, unless you only use swap very seldom. It will be slower but last longer with swap on the HDD. If you use swap very seldom, it does not cost much to have slower swap on the HDD. Do you intend to hibernate? Then you need at least as much swap as RAM in Gibibytes, otherwise it is probably enough with 1 or 2 GB (size of swap partition).

---

### Post by newb85 on 2014-07-10
Would it not be better to let Ubuntu use a swap file instead?  It would be on the SSD, so faster, but TRIM would keep it from wearing a specific spot.

---

### Post by sudodus on 2014-07-10
> **newb85 said:**
> Would it not be better to let Ubuntu use a swap file instead?  It would be on the SSD, so faster, but TRIM would keep it from wearing a specific spot.

Yes, it is possible, would be better than a swap partition on the SSD, but still produce wear. I'm not sure but think it must be created and removed at each boot to give TRIM a chance to work. I'd say a swap file is a good alternative, if you have a lot of swapping and need the speed of the SSD, and are prepared to pay the price of wear. An alternative is to install more RAM to reduce swapping or have swap in RAM (for example zRAM).

These are advanced alternatives, that can be tried later on, when the other parts of the installed system are working well.

---

### Post by oldfred on 2014-07-10
If you have a new computer, you should have enough RAM to not normally use swap. I have 4GB on my system from 2006 (it was a lot then) and almost never use swap.
If a new SSD many now say that they have lives similar to hard drives. Not forever but you should not have to worry.
I have a older slow SSD and just have swap on hard drive, but never see it used. You actually do not want swap used as it is many times slower than RAM even if on SSD.

I prefer to partition in advance with gparted. But if not also installing Windows or if a new system and you may want now or later UEFI, you need to use gpt partitioning. Windows only boots from gpt with UEFI, but Ubuntu can use either BIOS or UEFI if correct supporting partitions are on drive. 
  I use gparted and select gpt under device, advanced & select gpt over msdos(MBR) default partitioning....
I also suggest including an efi partition at beginning of hard drive also. Then you can put a test install on hard drive and make it bootable on its own. Then if issues with SSD you can still boot hard drive.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

I am reusing an old test install and examples are selecting existing partition with change button on sdc and sdd drives. So you can select any partition and choose that for any system folder mount.

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by chris-burmajster on 2014-07-11
> [COLOR=#000000]You must also decide where to put the swap partition. It will be faster on the SSD, but will wear it, unless you only use swap very seldom. It will be slower but last longer with swap on the HDD. If you use swap very seldom, it does not cost much to have slower swap on the HDD. Do you intend to hibernate? Then you need at least as much swap as RAM in Gibibytes, otherwise it is probably enough with 1 or 2 GB (size of swap partition).[/COLOR]

Thank you all for your informative replies!

The computer I will be buying will have 16Gb of RAM, so maybe I'll do without a swap file, as a number of you have suggested. Generally I don't use hibernate, as my present computer is so old (8 years) that it plays up if I try to do fancy things with it; it originally came with Windows XP. It responds well to a clean boot. For practice I have backed up my laptop and will wipe it tonight so that I can re-install it and get some practice with the 'something else' option. I have just upped the RAM from 2 to 4GB (the maximum the motherboard will take), so I plan to install the 64bit version of 14.04 to take advantage of the extra RAM. So, hopefully, once the new desktop arrives at the end of the month, I'll know what I'm doing.

Thank you all for your help - much appreciated!

Chris

---

### Post by oldfred on 2014-07-11
Some examples with screen shots:

With UEFI & Windows 8 you do have to do several things in advance. You must turn off fast boot in Windows and maybe in UEFI, and usually better to turn off secure boot.
Backups are very important as reinstall now seems to overwrite Windows unless you use Something Else.
Links to many other good UEFI install sites in link in my signature.


 Install to external drive. Also any second drive. Or any install with Something Else
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):



UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

---

