---
title: "Windows 7 RC 7100 and Ubuntu 9.04, dual booting"
date: 2009-06-05
forum: Outdated Tutorials &amp; Tips
---

### Post by nucleuskore on 2009-06-05
[PDF version of this guide](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/dualboot_windows_7_RC7100_Ubuntu_Jaunty_2009.pdf)
-------------------------------------------------------------------------------------------------------------
This is a copy of the tutorial published on my website on 
[img]http://i.creativecommons.org/l/by-nc-sa/2.5/in/88x31.png[/img]
This work is licensed under a [Creative Commons Attribution-Noncommercial-Share Alike 2.5 India License](http://creativecommons.org/licenses/by-nc-sa/2.5/in/)

[size=+2]**Foreword and Introduction:**[/size]
On the 21st of August, 2008, I released my [first tutorial](http://ubuntuforums.org/showthread.php?t=899222) on dual booting Windows XP and Ubuntu/OpenSUSE Linux. The tutorial was well received, too well I must say, judging from the number of hits, and the feedback I received. Although Windows Vista was the prevalent OS at the time, I refrained from writing a tutorial on dual booting with Vista as I personally felt that it was another Windows ME. A lot of water has flown under the bridge since then, and we now have a shiny new Windows OS in the form of Windows 7 (RC 7100 at the time of writing this tutorial), which I must say, looks and feels far better than it's predecessor. A month back Canonical also released their new version of their flagship OS, Ubuntu 9.04. This tutorial is intended to guide newcomers on partitioning and installing Windows 7 RC 7100 and Ubuntu 9.04 on their new or existing PCs.

One of the important differences between this tutorial and my earlier one with Windows XP is the compulsory use of a third party bootloader in dualbooting with Windows 7/Linux, due to issues using GRUB on the MBR. If this is too technical for you to understand don't bother, just follow my tutorial step by step and you'll be fine. As before, I have used a lot of screenshots, and I would strongly recommend that you either have a hard copy of this in hand before you start, or have it open on another system.

[size=+2]**Assesing your hard disk, partitions**[/size]
While installing Windows 7 to a new/clean hard disk, you might have noticed that the installer automatically creates a system partition BEFORE the C: drive as shown below.
[[img]http://img404.imageshack.us/img404/7669/snapshot10.th.png[/img]](http://img404.imageshack.us/my.php?image=snapshot10.png)[[img]http://img2.imageshack.us/img2/7282/snapshot11b.th.png[/img]](http://img2.imageshack.us/my.php?image=snapshot11b.png)
The system reserved partitin should not be disturbed, lest your Windows become unbootable. You cannot see this partition when you open My Computer in Windows 7.

To install linux on your PC you should first make some free space available on your hard disk for the install. Click on Start->Control Panel->System and Security->and Under Administrative tools click on "Create and format hard disk partitions"

[[img]http://img197.imageshack.us/img197/4643/snapshot13.th.png[/img]](http://img197.imageshack.us/my.php?image=snapshot13.png)[[img]http://img3.imageshack.us/img3/3739/snapshot14.th.png[/img]](http://img3.imageshack.us/my.php?image=snapshot14.png)[[img]http://img383.imageshack.us/img383/6391/snapshot15.th.png[/img]](http://img383.imageshack.us/my.php?image=snapshot15.png)

I present two hypothetical scenarios that you might have. The actual partition sizes will vary with the capacity of the hard disk. I have taken a 160 GB hard disk in my example.
[list][*]You only have one C partition of 20 GB and the remaining part of your hard disk is "unallocated" as shown below
[[img]http://img3.imageshack.us/img3/9804/snapshot16.th.png[/img]](http://img3.imageshack.us/my.php?image=snapshot16.png)
[*]Your full hard disk is occupied by windows partitions as shown below
[[img]http://img197.imageshack.us/img197/1789/snapshot94.th.png[/img]](http://img197.imageshack.us/my.php?image=snapshot94.png)[/list]

---

### Post by nucleuskore on 2009-06-05
If your partitioning scenario resembles the first (I'll refer to it as scenario 1 from now on), then you have a lot of free space on your hard disk to do as you please. You may allot more space to Windows 7 by right clicking on the unallocated space and creating new partitions, or you may use the entire unallocated space for Ubuntu. However it is more likely that your hard disk partition set up resembles scenario 2 :) In that case you have to right click on one or more of the partitions at the end to free up space to install Ubuntu. First back up the data on the partition you want to delete, and then right click on the partition and delete it as shown below.

[[img]http://img208.imageshack.us/img208/6302/snapshot95.th.png[/img]](http://img208.imageshack.us/my.php?image=snapshot95.png) [[img]http://img41.imageshack.us/img41/5457/snapshot96.th.png[/img]](http://img41.imageshack.us/my.php?image=snapshot96.png) [[img]http://img36.imageshack.us/img36/7923/snapshot97.th.png[/img]](http://img36.imageshack.us/my.php?image=snapshot97.png)

Note the colour code that Windows Disk Management System uses for various partitions, dark blue for primary partitions, deep green for the extended partition (see the rim around E: and F:), light blue for logical partitions, and light green for free space. Know this, that there can only be four primary partitions in a hard disk. If you would like to have more than four partitions, you have to use logical partitions as has happened in scenario 2. Windows and linux use different ways of naming partitions. While you would just refer to partitions as C:, D:, E:, etc in Windows, A; and B: being reserved for floppy drives, in Linux we refer to them as /dev/sda1, /dev/sda2, etc. for the first, second, and subsequent hard disk partitions. As you can see, in scenario 2, the first partition is a System Reserved partition, and windows has not assigned it any drive letter (alphabet like A, B, C, or anything else). However, linux will not make such a distinction, the first partition is always /dev/sda1, and so in the case of Windows Vista or Windows 7 being your first/primary OS, the C: drive will actually correspond to /dev/sda2, as the first partition, /dev/sda1 is a System reserved partition. Now, I told you that we can have only four primary partitions in a hard disk. So for linux, these would be /dev/sda1, /dev/sda2, /dev/sda3, and /dev/sda4. The first logical partition would number from /dev/sda5, /dev/sda6, etc. This is why linux ALWAYS assigns /dev/sda5 to the first logical partition, irrespective of the number of partitions preceding that.

The idea is to free at least 20 GB for our linux install. This might seem like a lot and other's might disagree, but if you are looking for a full experience I'd recommend it. We will later need this space for creating three partitions.

Swap - Space=1.5 to 2 times your RAM
Root (designated as /) - stores your OS and system files, programs, etc. - Minimum space approx 8GB
Home (designated as /home) - like the Documents and Settings folder of Windows XP or the Users folder of Windows 7. Stores your preferences, bookmarks, wallpaper, My Documents and Desktop. - Space - remaining space

The / is like the base directory in linux, into which all other directories (folders) are incorporated or "mounted". I took a very long time to understand the concept of "mounting". Don't worry about it for now, you will understand when the time is right.

**Resizing Partitions** is something I do not recommend with any tool unless you have **uninterrupted power supply** in your part of the country/world or a power back up solution that lasts for a few hours.

[size=+2]**_Hardware check_**[/size]
With the advances in Linux and the new kernels this step may not be necessary, but will help you in troubleshooting later if required.
Click on Start->Control Panel->System and Security->System->Device Manager
Make a note of the model numbers of your monitor, graphics card (display adapter), and any other devices.

If possible, note the horizontal and vertical sync values of your monitor. These can be found in the manual of the monitor and may be required should you have display problems.
Alternatively you can use a third party software like SiSoft Sandra Lite to probe your hardware and make a list by hand.

[size=+2]**_Installing Ubuntu Linux_**[/size]
You are now going to install Ubuntu Linux to the empty space on your hard disk that you prepared in the earlier step. Linux by itself is not a single monolithic entity unlike some popular operating systems. It is very much a collaborative effort. It consists of a core (also called a kernel) on which the entire system is built on an runs. Linux is modular. As you become more experienced, you will realise that you can add and remove modules depending on your requirement and create a highly customised system. No hidden agandas, no long cryptic EULAs (the thingy which you blindly scroll down and click "I agree" without batting an eyelid) - just freedom.

[size=+2]**_So let's get started !!_**[/size]

Ubuntu CDs are available for free from [SHIPIT](https://shipit.ubuntu.com)
You can also download it from [Ubuntu website](http://www.ubuntu.com/) or ask a LUG (Linux User Group) near you. 

To boot from the cd or dvd your bios should have it as the first boot device. Alternatively some bios allow you to select the boot device. The key used for this varies with different manufacturers. To see if your bios has a boot device select menu please refer the manual of your motherboard or take help from a more experienced friend. 

I suggest you try the following - insert the cd or dvd and start your pc. If your pc boots too fast simply restart windows with the cd or dvd in the drive and see what happens. Very often the optical drive would have been set as the first boot device and the system boots from the cd automatically. If it still goes to windows and refuses to boot from your cd or dvd then you will have to adjust your bios settings or search for a boot menu as I described earlier.

If your pc boot successfully from your ubuntu cd you will see this screen

[[img]http://img197.imageshack.us/img197/8640/snapshot17.th.png[/img]](http://img197.imageshack.us/my.php?image=snapshot17.png)

It is prompting you to select the language. Use your arrow keys to select the system language and press ENTER. You will then get this screen

[[img]http://img205.imageshack.us/img205/7373/snapshot18.th.png[/img]](http://img205.imageshack.us/my.php?image=snapshot18.png)

Use the Up and Down arrow keys on your keyboard to select the option Install Ubuntu and press ENTER. The system will start booting.

[[img]http://img197.imageshack.us/img197/6522/snapshot19.th.png[/img]](http://img197.imageshack.us/my.php?image=snapshot19.png)

---

### Post by nucleuskore on 2009-06-05
You will see the Welcome screen in your language. Make sure your language selection is right and click forward

[[img]http://img193.imageshack.us/img193/7025/snapshot20.th.png[/img]](http://img193.imageshack.us/my.php?image=snapshot20.png)

Select your timezone from the list, it is arranged by continent, and click forward

[[img]http://img504.imageshack.us/img504/619/snapshot21.th.png[/img]](http://img504.imageshack.us/my.php?image=snapshot21.png)

Select your keyboard type, most common is US International (see picture below), but make sure and use the test box made available to you to check your selection. If it does not work try USA -International with AltGr dead keys like I have. I advise you to select this if you use US Intl in India. Check not only for alphabets, capital and small, but also for special characters like ' " ? / + ; If all these are correct then your choice of keybord layout is fine, click forward

[[img]http://img151.imageshack.us/img151/2249/snapshot22.th.png[/img]](http://img151.imageshack.us/my.php?image=snapshot22.png)

You will now be presented with the partitioning options. Ubuntu "intelligently" offers to resize your windows partition and do everything automatically. I advise AGAINST using this option, and instead select the manual option and click forward

[[img]http://img197.imageshack.us/img197/796/snapshot23.th.png[/img]](http://img197.imageshack.us/my.php?image=snapshot23.png) [[img]http://img177.imageshack.us/img177/18/snapshot24.th.png[/img]](http://img177.imageshack.us/my.php?image=snapshot24.png)

You will now come to a screen which shows you the layout of partiitons on your hard disk. Just as I mentioned earlier, note the nomenclature used in linux. The first hard disk is labelled as /dev/sda Partitions within this are labelled as /dev/sda1 /dev/sda2 so on and so forth. /dev/sda2 is the C drive and has an ntfs filesystem, whereas /dev/sda1 is the system reserved partition and has no drive letter.

[[img]http://img168.imageshack.us/img168/4792/snapshot25.th.png[/img]](http://img168.imageshack.us/my.php?image=snapshot25.png)
[[img]http://img245.imageshack.us/img245/5307/snapshot26.th.png[/img]](http://img245.imageshack.us/my.php?image=snapshot26.png) **or** [[img]http://img192.imageshack.us/img192/3308/snapshot98.th.png[/img]](http://img192.imageshack.us/my.php?image=snapshot98.png)

---

### Post by nucleuskore on 2009-06-05
How you proceed from here will now depend on your existing hard disk partitions, and how much space you are willing to allot for Ubuntu.  
Select free space and click on the "New Partition" button as shown below

Scenario 1
[[img]http://img140.imageshack.us/img140/2099/snapshot27.th.png[/img]](http://img140.imageshack.us/my.php?image=snapshot27.png)
Scenario 2
[[img]http://img192.imageshack.us/img192/3308/snapshot98.th.png[/img]](http://img192.imageshack.us/my.php?image=snapshot98.png)

Select type of partition logical, size 20000 MB (scenario 1) or 20000 MB (scenario 2), location for new partition Begining, Use as: Ext 4 journaling file system, mount point: / and click OK

Scenario 1
[[img]http://img3.imageshack.us/img3/3149/snapshot28.th.png[/img]](http://img3.imageshack.us/my.php?image=snapshot28.png)
Scenario 2
[[img]http://img4.imageshack.us/img4/5215/snapshot991.th.png[/img]](http://img4.imageshack.us/my.php?image=snapshot991.png)

The proposed partition table layout will get updated as shown below:
<table>Scenario 1

[[img]http://img189.imageshack.us/img189/4580/snapshot31.th.png[/img]](http://img189.imageshack.us/my.php?image=snapshot31.png)
Scenario 2
[[img]http://img140.imageshack.us/img140/2817/snapshot992.th.png[/img]](http://img140.imageshack.us/my.php?image=snapshot992.png)

Again select free space and click New Partition. Select type of partition logical, size: Note the size mentioned, and subtract the amount of space you would like to dedicate to the swap partition. In my case I subracted 1000 MB from that figure. Swap space is recommended to be 1.5 times the amount of RAM you have, so if you have 1 GB RAM, 1-1.5 GB swap should do. Location for new partition Begining, Use as: Ext 4 journaling file system, mount point: /home and click OK. Note that you will manually have to type in the mount point in the box provided as /home

Scenario 1
[[img]http://img37.imageshack.us/img37/1654/snapshot32.th.png[/img]](http://img37.imageshack.us/my.php?image=snapshot32.png)[[img]http://img188.imageshack.us/img188/2260/snapshot33.th.png[/img]](http://img188.imageshack.us/my.php?image=snapshot33.png)

---

### Post by nucleuskore on 2009-06-05
Scenario 2
[[img]http://img140.imageshack.us/img140/2817/snapshot992.th.png[/img]](http://img140.imageshack.us/my.php?image=snapshot992.png)[[img]http://img404.imageshack.us/img404/6298/snapshot993.th.png[/img]](http://img404.imageshack.us/my.php?image=snapshot993.png)

The proposed partition table layout will get updated as shown below:
Scenario 1

[[img]http://img37.imageshack.us/img37/9807/snapshot34.th.png[/img]](http://img37.imageshack.us/my.php?image=snapshot34.png)
Scenario 2
[[img]http://img197.imageshack.us/img197/1017/snapshot100.th.png[/img]](http://img197.imageshack.us/my.php?image=snapshot100.png)

Again select free space and click New Partition. Select type of partition logical, size: no change if it is roughly 1.5 times your RAM, location for new partition Begining, Use as: swap area, and click OK
Scenario 1

[[img]http://img193.imageshack.us/img193/4596/snapshot35.th.png[/img]](http://img193.imageshack.us/my.php?image=snapshot35.png)
Scenario 2
[[img]http://img192.imageshack.us/img192/8541/snapshot101.th.png[/img]](http://img192.imageshack.us/my.php?image=snapshot101.png)

This is how your proposed partition table layout finally looks like.

Scenario 1:
[[img]http://img36.imageshack.us/img36/477/snapshot36.th.png[/img]](http://img36.imageshack.us/my.php?image=snapshot36.png)

Scenario 2:
[[img]http://img149.imageshack.us/img149/1616/snapshot102.th.png[/img]](http://img149.imageshack.us/my.php?image=snapshot102.png)

Remember, nothing has actually happened to your partitions as yet, this is just a proposed layout, so if you make a mistake in your newly created linux partitions you can simply go back and redo the partitioning. Make a note of all the partitions (numbers) on a piece of paper, especially the root partition.

Before you click Forward visit this post. I forgot something when I first wrote this tutorial
[http://ubuntuforums.org/showthread.php?p=7458064#19](http://ubuntuforums.org/showthread.php?p=7458064#19)

---

### Post by nucleuskore on 2009-06-05
Click Forward. You will now be asked some details about yourself. You will have to give a password. Make sure you don't forget it. Click Forward

[[img]http://img34.imageshack.us/img34/993/snapshot37.th.png[/img]](http://img34.imageshack.us/my.php?image=snapshot37.png)

If your password is not strong you'll get the following prompt. You may choose to ignore it and continue or go back and change your password.
[[img]http://img36.imageshack.us/img36/7623/snapshot38.th.png[/img]](http://img36.imageshack.us/my.php?image=snapshot38.png)

Import your windows settings. This is optional you can leave it unchecked and click forward. There is a chance that this step may not appear.

You will now be presented with an overview of the install parameters. Before you proceed you will have to change the install location of the GRUB bootloader which will otherwise get installed to the MBR, and everything will go to hell.

[[img]http://img189.imageshack.us/img189/3930/snapshot391.th.png[/img]](http://img189.imageshack.us/my.php?image=snapshot391.png)

Click Advanced, and in the dialog box that opens click on the dropdown list and select your root partition, and click OK.

[[img]http://img30.imageshack.us/img30/2736/snapshot392.th.png[/img]](http://img30.imageshack.us/my.php?image=snapshot392.png)
&nbsp [[img]http://img10.imageshack.us/img10/2460/snapshot393.th.png[/img]](http://img10.imageshack.us/my.php?image=snapshot393.png)

---

### Post by nucleuskore on 2009-06-05
Click Install, the installation will begin with the formatting and copying of files to your hard disk.

[[img]http://img141.imageshack.us/img141/7547/snapshot40.th.png[/img]](http://img141.imageshack.us/my.php?image=snapshot40.png) &nbsp
[[img]http://img3.imageshack.us/img3/4356/snapshot41i.th.png[/img]](http://img3.imageshack.us/my.php?image=snapshot41i.png)&nbsp
[[img]http://img99.imageshack.us/img99/6467/snapshot42.th.png[/img]](http://img99.imageshack.us/my.php?image=snapshot42.png)

At the end of installation click on the Restart Now button

[[img]http://img36.imageshack.us/img36/6109/snapshot44.th.png[/img]](http://img36.imageshack.us/my.php?image=snapshot44.png)

As the system shuts down, you will get a message telling you to remove the cd from the drive and press ENTER to reboot the system, which you must do.

Your PC will boot directly to Windows, as the GRUB bootloader has been installed to the root partition. We will now have to install a third party bootloader, the GAG bootloader.
[url=http://gag.sourceforge.net/download.html" target="_blank"><blink>Download the GAG bootloader</blink></a>

Your PC will boot directly to Windows, as the GRUB bootloader has been installed to the root partition. We will now have to install a third party bootloader, the GAG bootloader.[url=http://gag.sourceforge.net/download.html" target="_blank"><blink>Download the GAG bootloader</blink></a>

Unzip the archive to a folder, and write the cdrom.iso image to a cd. Boot from the cd. You will get this screen.

[[img]http://img208.imageshack.us/img208/4005/snapshot67.th.png[/img]](http://img208.imageshack.us/my.php?image=snapshot67.png)

Press 4 to install GAG. You will get this screen

[[img]http://img245.imageshack.us/img245/3206/snapshot68.th.png[/img]](http://img245.imageshack.us/my.php?image=snapshot68.png)

Select your keyboard (usually 1 in India)

then your language, 8

[[img]http://img3.imageshack.us/img3/3238/snapshot69.th.png[/img]](http://img3.imageshack.us/my.php?image=snapshot69.png)

You will then come to this screen. press S to setup the bootloader

[[img]http://img13.imageshack.us/img13/4139/snapshot70.th.png[/img]](http://img13.imageshack.us/my.php?image=snapshot70.png)

---

### Post by nucleuskore on 2009-06-05
The alphabets you have to press to execute a function are highlighted in red in the GAG set up screen. Keys are case insensitive. Press A to add an operating system

[[img]http://img4.imageshack.us/img4/9418/snapshot71.th.png[/img]](http://img4.imageshack.us/my.php?image=snapshot71.png)

As you can see, partition A is the floppy, B is the first ntfs windows partition (which is the boot, system reserved in Windows 7), and the second ntfs windows partition is C, so press <b>B</b>

[[img]http://img207.imageshack.us/img207/5145/snapshot72.th.png[/img]](http://img207.imageshack.us/my.php?image=snapshot72.png)

You will now have to type a name, say Windows 7
[[img]http://img514.imageshack.us/img514/5568/snapshot73.th.png[/img]](http://img514.imageshack.us/my.php?image=snapshot73.png)

You will have to now type a password, optionally, so press ENTER to avoid giving one
[[img]http://img205.imageshack.us/img205/5876/snapshot74.th.png[/img]](http://img205.imageshack.us/my.php?image=snapshot74.png)

You now have to select an icon, Press C for windows
[[img]http://img13.imageshack.us/img13/3540/snapshot75.th.png[/img]](http://img13.imageshack.us/my.php?image=snapshot75.png)

Now you will come back to this screen
[[img]http://img504.imageshack.us/img504/876/snapshot76.th.png[/img]](http://img504.imageshack.us/my.php?image=snapshot76.png)

Press A to add an operating system

[[img]http://img4.imageshack.us/img4/9418/snapshot71.th.png[/img]](http://img4.imageshack.us/my.php?image=snapshot71.png)

Now if you remember the first partition you made for linux was root (/), to which we installed GRUB. So the alphabet you have to press corresponds to the first "LINUX EXT2" partition in the list you see onscreen. Do that. Simple !

You will now have to type a name, say Linux
[[img]http://img353.imageshack.us/img353/9378/xp60ro3.th.png[/img]](http://img353.imageshack.us/my.php?image=xp60ro3.png)

---

### Post by nucleuskore on 2009-06-05
You will have to now type a password, optionally, so press ENTER to avoid giving one
[[img]http://img205.imageshack.us/img205/5876/snapshot74.th.png[/img]](http://img205.imageshack.us/my.php?image=snapshot74.png)

You now have to select an icon, Press D for Linux
[[img]http://img13.imageshack.us/img13/3540/snapshot75.th.png[/img]](http://img13.imageshack.us/my.php?image=snapshot75.png)

Now you will come back to this screen
[[img]http://img504.imageshack.us/img504/876/snapshot76.th.png[/img]](http://img504.imageshack.us/my.php?image=snapshot76.png)

Press H to save in the hard disk, you will get this message, press ENTER

[[img]http://img3.imageshack.us/img3/2643/snapshot77.th.png[/img]](http://img3.imageshack.us/my.php?image=snapshot77.png)

Press R to return to the main menu, you should see this

[[img] http://img149.imageshack.us/img149/7759/snapshot79.th.png[/img]]("http://img149.imageshack.us/my.php?image=snapshot79.png")

Extra options in the setup include setting a timer for a default OS to boot.
Read the index.html file in the docs folder of the gag file you downloaded.
[size="+5"]All the best !!![/size]

---

### Post by forrestcupp on 2009-06-05
Wow.  That's pretty thorough.  I think there's a section here specifically for howto's.

Thanks for putting that much work into this, though.

---

### Post by Sealbhach on 2009-06-05
Terrific work there, well done. =D>

.

---

### Post by nucleuskore on 2009-06-05
Thanks for the encouragement :)

> **forrestcupp said:**
> Wow.  That's pretty thorough.  I think there's a section here specifically for howto's.

My first tutorial was put here by the MODS
[http://ubuntuforums.org/showthread.php?t=899222](http://ubuntuforums.org/showthread.php?t=899222)

so I started it here :)

---

### Post by meborc on 2009-06-05
> **nucleuskore said:**
> Thanks for the encouragement :)



My first tutorial was put here by the MODS
[http://ubuntuforums.org/showthread.php?t=899222](http://ubuntuforums.org/showthread.php?t=899222)

so I started it here :)

yes, but you should actually ask mods to move this to the tutorials and tips section... there is a lot of traffic here at the community cafe and your thread can "disappear" soon under new threads...

---

### Post by cariboo on 2009-06-06
New tutorial, just to bump it to the top of the page

---

### Post by SaddaGocaraRupa on 2009-06-06
Great tutorial, thank you!

Will this work with an existing dual-boot install? I'm currently running Vista x64/Intrepid (via Wubi on the Windows partition). Can I simply format the HDD via the Windows 7 installer or will this break GRUB?

Cheers,

-Sadda-

---

### Post by nucleuskore on 2009-06-06
Sorry, I really have no idea about Wubi.

---

### Post by forrestcupp on 2009-06-06
> **SaddaGocaraRupa said:**
> Great tutorial, thank you!

Will this work with an existing dual-boot install? I'm currently running Vista x64/Intrepid (via Wubi on the Windows partition). Can I simply format the HDD via the Windows 7 installer or will this break GRUB?

Cheers,

-Sadda-

It will break Grub, but if you do a search here, Grub isn't really hard to restore.  I have no idea how it works with Wubi, though.  But if you're going to use this tutorial, you might as well do a real dual boot instead of using Wubi.

From my limited knowledge of Wubi, I really don't like its concept.  It seems that if your Windows install gets trashed, you'll lose your Linux install, too.  Dual booting is really not much harder of a task, and I think it's probably worth it.

But if you're going to format your whole hard drive, you'll lose everything and have to start over.  You'll install Win7 first, which will wipe out Grub and use Windows BCD to boot.  Then you'll install Ubuntu, which will install Grub for you and use that before the Windows bootloader.  So you're pretty much starting from scratch.

---

### Post by forrestcupp on 2009-06-06
> **SaddaGocaraRupa said:**
> Great tutorial, thank you!

Will this work with an existing dual-boot install? I'm currently running Vista x64/Intrepid (via Wubi on the Windows partition). Can I simply format the HDD via the Windows 7 installer or will this break GRUB?

Cheers,

-Sadda-

It will break Grub, but if you do a search here, Grub isn't really hard to restore.  I have no idea how it works with Wubi, though.  But if you're going to use this tutorial, you might as well do a real dual boot instead of using Wubi.

From my limited knowledge of Wubi, I really don't like its concept.  It seems that if your Windows install gets trashed, you'll lose your Linux install, too.  Dual booting is really not much harder of a task, and I think it's probably worth it.

But if you're formatting you're whole hard drive, you'll lose everything and have to start from scratch.  You'll have to install Windows7 first, then reinstall Ubuntu.  So if you follow this tutorial, it doesn't matter what happens to Grub; it will be reinstalled at the end.


Just never forget that the Windows 7 RC expires next July and you'll have to either buy the full version or reinstall Vista.  Then you'll have to worry about restoring Grub again. :)

---

### Post by nucleuskore on 2009-06-14
-------------------------------------------------------------------------------------------------------------
**Edit: **
Mounting Windows partitions:
This is something I forgot to write about in the original tutorial. Note your windows partitions and filesystems in the partition table. They will be marked as ntfs or vfat/fat32. If you have a 100 MB fist partition as is the case here, skip it as this is the boot partition (/dev/sda1). Select on /dev/sda2 or as is in this case, /dev/sda5 and click edit partition.
[[IMG]http://img257.imageshack.us/img257/7830/snapshotw1.th.png[/IMG]](http://img257.imageshack.us/i/snapshotw1.png/)

Against Use as:, click Do not use this partition and change the filesystem to ntfs or fat32, depending on what you read in the proposed partition layout. It is ntfs in this case. **Make sure that you do not tick Format this partition.**
[[IMG]http://img199.imageshack.us/img199/4037/snapshotw2.th.png[/IMG]](http://img199.imageshack.us/i/snapshotw2.png/) [[IMG]http://img395.imageshack.us/img395/9899/snapshotw3.th.png[/IMG]](http://img395.imageshack.us/i/snapshotw3.png/)

Enter a suitable mount point. In this case I have entered /windows/c as this is my C drive in Windows 7.
[[IMG]http://img36.imageshack.us/img36/9293/snapshotw4.th.png[/IMG]](http://img36.imageshack.us/i/snapshotw4.png/) [[IMG]http://img41.imageshack.us/img41/8821/snapshotw5.th.png[/IMG]](http://img41.imageshack.us/i/snapshotw5.png/)

Repeat the above steps for each windows partiiton assigning new mount points for each, so that the final proposed partition layout looks like this
[[IMG]http://img199.imageshack.us/img199/6325/snapshotw6.th.png[/IMG]](http://img199.imageshack.us/i/snapshotw6.png/)
End Edit
---------------------------------------------------------------------------------------------------------------
Continue [http://ubuntuforums.org/showthread.php?t=1179194#6](http://ubuntuforums.org/showthread.php?t=1179194#6)

---

### Post by H2SO_four on 2009-06-14
Great write up! will come in handy for sure

---

