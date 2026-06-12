---
title: "How to Partition, etc. in Windows 8"
date: 2013-02-09
forum: New to Ubuntu
---

### Post by c5vetter on 2013-02-09
Okay, got Ubuntu 12.10 and have attempted to install, but am having problems. So, went back to basic Windows 8 with nothing else loaded.

Got to Computer Management and here is what "C" drive looks like for partitions:

400M Healthy (Recovery partition)
260M Healthy (EFI system partition)
5.47G (Healthy primary partition)
171.16G (Healthy - C drive NTFS partition)
393.46G (Unallocated space)


So, when I insert the 12.10 DVD in and click restart will Ubuntu be installed in the unallocated space? Will I be prompted to set-up a partition for Ubuntu?

In case you can't tell I am learning this as I go!

---

### Post by arpanaut on 2013-02-09
Basics:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Additional info:
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=uefi+%2B+oldfred&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=uefi+%2B+oldfred&as_qdr=all&sa=Google+Search&lang=en)

Good Luck, Many things have changed with uefi, Win 8, restricted boot.

---

### Post by oldfred on 2013-02-09
With UEFI there is a major choice as you start. How you boot install media is how it will install and there are two modes, one UEFI and the other BIOS/legacy/AHCI/CSM or whatever. You have to install Ubuntu in UEFI mode to easily dual boot. But a few systems will not install in UEFI mode (or must be in BIOS mode). Boot-Repair can convert BIOS mode install to UEFI mode if not installed correctly.

Ubuntu will then give several choices. One is overwrite entire drive which you almost never want. One choice should be to install into unallocated space. And you have Something else which you need if you want to specify partitions manually, include more partitions like /home than the default of / (root) and swap.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

    You will need Boot-Repair to fix a bug in grub that does not create correct Windows entries.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

    
Some Samsungs have been bricked by just booting Ubuntu (but also by some Windows software?). Seems to be mostly a Samsung bug in its UEFI.
       [https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop)
Booting the Ubuntu installer in UEFI mode from a USB disk on certain Samsung laptops (530U3C, NP700Z5C) may trigger a firmware bug that renders the machine unbootable. Users are advised to use caution when installing on Samsung laptops and ensure that they are configured for legacy BIOS mode, not UEFI mode. (1040557) 

    What model computer is it. Some just work, some require some effort (especially with Intel SRT) and others just about are impossible to do.

Some that have worked.
       Dell XPS13 Details on how to install - UEFI and Intel SRT  in Post #10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)

    
I prefer smaller system partitions of 25GB and separate data or /home. With Windows 8 a separate shared NTFS data partition is just about required, but you should turn off fast boot or the hibernation it uses.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by c5vetter on 2013-02-10
Okayu - thanks for the suggestions! Was able to finally get 12.10 installed and configured on my HP Envy. Start the computer and Ubuntu comes up FAST! But, now the next question - how do I get Windows 8 to show up as a choice? Do not see a choice for Windows, comes straight to Ubuntu.

---

### Post by thermion on 2013-02-10
> **c5vetter said:**
> Okayu - thanks for the suggestions! Was able to finally get 12.10 installed and configured on my HP Envy. Start the computer and Ubuntu comes up FAST! But, now the next question - how do I get Windows 8 to show up as a choice? Do not see a choice for Windows, comes straight to Ubuntu.

That depends a bit on your setup. If you are using UEFI and installed grub to the UEFI partition, then you have to chose to boot your windows installation from the UEFI boot menu.

---

### Post by oldfred on 2013-02-10
Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by c5vetter on 2013-02-13
Okay, finally got around to doing the Boot Repair and the report it generated is:  paste.ubuntu.com/1647711

Bios boot on sda4/efi/ubuntu/grubx64.efifile

Also, stated the boot files of the OS now in use - Ubuntu 12.10 are far from the start of the disk. Your Bios may not detect them. You may want to retry after creating a /boot/efi partition (FAT 32, 100mb - 250mb, start of the disk boot flag). This can be performed via tools such as gPartd. Then select partition in the [separate/boot/efi partitionoption of Boot Repair]

Also, attempted to install some software and was told I had run out of space or was running out of space in /??????? WTFO, have 750gb hard drive!? So, guess something is definitely fishy in Holland!

---

### Post by oldfred on 2013-02-13
@boarder28
Moved to your own thread. Please do not highjack an unrelated thread.

> =================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
[COLOR=Red]/dev/sda2      ext4      3.7G  2.8G  776M  79% /[/COLOR]
udev           devtmpfs  2.7G   12K  2.7G   1% /dev
tmpfs          tmpfs     1.1G  860K  1.1G   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     2.7G  156K  2.7G   1% /run/shm
none           tmpfs     100M   64K  100M   1% /run/user
/dev/sda3      ext4      230G  271M  218G   1% /home
/dev/sda1      ext4      2.8G  120M  2.5G   5% /boot
/dev/sda4      vfat       33M  122K   33M   1% /boot/efi


I normally suggest 10 to 25GB for / (root) and you gave it 3.7GB. With most new desktops and a smaller / you normally do not need a separate /boot. The UEFI specification says the efi partition should be first (but most Windows seem to make it second or third). But I think it is best near the start of the drive. Also efi partitions should be 100MB, and many suggest 200MB.

---

### Post by boarder428 on 2013-02-14
Sorry, didn't mean to hijack.  Thought it was a relevant question within this thread!

---

### Post by c5vetter on 2013-02-14
Okay - installed gparted and here is what I have

dev/sda1 ext4 /boot 2.7g
dev/sda2 ext 4 / 3.78g
dev/sda3 ext 4 /home 232.83g
dev/sda4 fat32 boot/efi 33.0m
dev/sda5 swap 2.79g
unallocated 354g

---

### Post by oldfred on 2013-02-14
That is what the df command from BootInfo report showed. Root is rather small but your /boot is large, but even combined it still would be a small / partition.

---

### Post by c5vetter on 2013-02-15
So, do I need to change size of partitions? Why do I get a statement like I am out of space when I am trying to get DROPBOX to install? Did I actually wipe out Windows 8 as I still do not see that as an option when I start the computer, as it goes direct to Ubuntu.

---

### Post by oldfred on 2013-02-15
There is no Windows partitions, nor recovery. So you must have chosen the install to entire hard drive option with the warning that it will erase your entire drive. 
If you still want Windows and did not do a backup before hand, you need to contact vendor and order new DVD image. Some vendors may charge.

Probably better just to reinstall. You have to move your /home right to make enough room for / (root). Then you can expand your / partition. You have to use gparted from a liveCD.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by c5vetter on 2013-02-15
So, I can NOT just use my Windows 7 DVD and install that, since I do NOT remember uninstalling or whatever Windows 8?

---

### Post by oldfred on 2013-02-15
Is your Windows 7 disk a full install, Vendor recovery or your own backup? 

If an install you will have to make at least one primary partition formatted NTFS with the boot flag or unallocated space with available primary partitions for Windows to install.

If a vendor recovery, you may just have to erase drive. Many Vendor recovery's are just an image of the hard drive as purchased.

If it is your own backup you have to recreate the partition that it was installed. Windows has information in the PBR partition boot sector that has to match partition table as to start & size of partition.

---

### Post by c5vetter on 2013-02-16
Full Windows installation disk - so, what do I need to do step-by-step please so I can make this work

---

### Post by oldfred on 2013-02-16
Do you want to erase the current Ubuntu and start over. Do you have anything in Ubuntu to backup?

Generally better to install Windows first but you do not have to. 

You do have to have an NTFS partition sda1 thru sda4 with the boot flag,  if installing in BIOS mode.

If UEFI it may want more partitions.

---

### Post by c5vetter on 2013-02-16
Don't really have anything in Ubuntu partitions - was just trying to get a dual-boot going and everything is FUBAR. So want to get back to good starting point which sounds like Windows first. So any step-by-step you can give me will be greatly appreciated

---

### Post by oldfred on 2013-02-16
Do not know about Windows other than this. It makes a huge difference if you install in UEFI mode or BIOS mode. You will have to delete the Linux partitions as Windows cannot see them. It needs unallocated space and available primary partitions or a NTFS formated partition if in BIOS mode. 

Windows will not boot in BIOS from gpt partitioned drive.

UEFI info:
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows 8 info
[http://technet.microsoft.com/en-us/library/hh824947.aspx](http://technet.microsoft.com/en-us/library/hh824947.aspx)


[URL="http://technet.microsoft.com/en-us/library/hh824947.aspx"]
[/URL]

---

### Post by c5vetter on 2013-02-17
Okay, still confused as to what I need to do!

How do I get back to a NTFS partition so I can get the Windows 7 disk to install? I believe I need that partition to do anything!?

All I have is Ubuntu partition, and when I start the computer it comes up with Ubuntu. I get error that am near end of disk and can not install anything else.

---

### Post by oldfred on 2013-02-17
You can use liveCD or flash and gparted from that to erase or change partitions. 

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

    
But you should be able to do everything from Windows. Windows does not really see Linux partitions but it should just let you reformat from its command line.

---

### Post by GregA on 2013-02-18
Hello C5,

Let me just say up front, I don't have the experience of Old Fred or other Ubuntu veterans, but here's the general direction of what I would do in your situation.

1.   First, I am "assuming" (because you did accomplish an Ubuntu install, albeit a poor one), that you did go back to "Legacy" bios via the PC setup process (so UEFI/Secure boot is no longer active in your settings).

2.   I would immediately download and burn an iso image of the "Parted Magic" Live Linux CD. Parted Magic will allow you to run "GParted" to repartition your messed up HD.  Also, Parted Magic (the Live CD), will run MUCH faster than most other rescue CD's, especially the Ubuntu Live CD, as it uses a lighter windows manager (openbox) and loads into your PC's RAM (when done loading into RAM, it will eject the CD as it's no longer needed).   This is a big deal, not only for speed, but because you now have a full OS to run your PC (as both your Windows and Linux installs are hosed).

3.   Open the GParted application (Partition Editor icon on the desktop).  Scan your HD, and delete all Linux partitions and the small Fat32 partion (sda4).  Now you should have a super large chunk of unallocated disk space.  Next, create a large "NTFS" partition for Win7.  Next, create a large ext4 partition for Linux.  Do not flag either partition as bootable.  Next, create a new swap partition for Linux of about 5 gigs.  It's OK to leave some unallocated space on the HD (I'd give Win about 250 gb, Linux about 150 gb, a small swap, and the rest unallocated).

4.  Save your changes, and exit GParted, then load your Win 7 DVD in the optical drive, and restart the system (use the normal Live CD exit-restart process).  See the Parted Magic website if you're unsure or unclear - - but I think it will be intuitive enough for you.   [http://partedmagic.com/doku.php#.USHGZn1KQWM](http://partedmagic.com/doku.php#.USHGZn1KQWM)

5.   Your PC will restart, and the Win7 DVD will have instructions about initiating the install/reinstall process.

6.   After Win 7 is successfully installed (including the Win boot manager), you should review the basic Ubuntu install process as documented at the Ubuntu site (for non-UEFI systems).  It's actually fairly easy to do a custom install and point the Ubuntu installer to use your large ext4 partion to install either Ubuntu (or as I did, "Kubuntu" as I prefer the standard PC gui environment over a modified PC/Tablet hybrid such as Ubuntu's Unity).  Note, be sure to let the Ubuntu bootloader (grub2), install to the MBR of sda0 or sda1 depending on what your drive looks like in GParted after the Win7 install.

The above info is a summary or rather high-level, but I think it points you in the right direction.

Old Fred or other experienced Ubuntuites - - pls correct anything in my post that's not right, or that I've omitted (such as, I'm not sure if C5 needs to run a MBR repair from the Win7 DVD to do a complete/succesful install).

---

### Post by oldfred on 2013-02-18
I have not installed Windows 7.

But Windows requires a boot flag to install. That way it knows which primary partition to use for the install and which to boot from.
Linux tools create valid NTFS partitions, but there are two versions. Linux tools create a XP type. I do not know if the Windows 7 installer converts automatically (I think so) or if you have to reformat. In Windows the makeactive command is used to set the boot flag, so if you did not do it in Linux you do it in Windows.

I had used chkdsk from a Windows 7 repair flash drive on my XP install. Chkdsk worked better but it converted PBR - partition boot sector from XP to Vista/7. Structure is different but you can see it says use ntldr with XP and bootmgr with Vista/7 in PBR if you view internal data.

---

### Post by c5vetter on 2013-02-22
Okay, new development - got Windows 7 PRO installed and it appears to be working fine. Now, I am installing Ubuntu 12.10. I am setting up the partitions and want to be sure they are correct before I INSTALL. Here is what I have:

free space - 1mb
/dev/sda1 - fat 32 - 104mb
/dev/sda2 - 134mb
/dev/sda3 - ntfs - 250gb
/dev/sda4 - swap - 5gb
free space 385gb

So, I know I need a Linux area - would that listed as "/" and about 150gb or would it be "/home" about 150gb - exactly what do I want to make it?

Know that I shoud NOT have a "/boot" is that correct?

---

### Post by Mark Phelps on 2013-02-23
Having a separate /home partition comes in handy when you want to upgrade and keep the stuff you already have in /home.  I used to have a bunch of partitions, including /boot, but over time, I shrunk down the number to just one "/" -- and that works fine.

Others may have different advice.

---

### Post by oldfred on 2013-02-23
For new users I often suggest a separate /home. That is easy to set up during install, but you still have to do Something Else or manual install to choose partitions and format of each partition.

But I have two separate data partitions one NTFS and the other Linux and do not have the separate /home as most of my data is in the data partitions. A bit more advanced as you have to plan partitions and mount partitions with fstab.

But with dual booting with Windows,  you should have a shared NTFS data partition whether you have a separate /home or not. Windows does not like to much activity from foreign systems. The Linux NTFS driver exposes all the hidden files & folder that Windows hides, so accidents are more likely. Better to set Windows system folder as read-only and use shared data for any data you may want in both systems.

       Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Mount NTFS partition:
[http://ubuntuforums.org/showthread.php?t=1927504](http://ubuntuforums.org/showthread.php?t=1927504)
Share Windows partition older:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

### Post by c5vetter on 2013-02-23
Okay - latest and greatest development - Windows 7 PRO and Ubunto 12.10 both are installed on my HP laptop. Used EasyBCD to make sure all the partitions were okay and that both would show up for choice at startup. SUCCESS so far! 

But,...................

When I chose Windows 7, loads and comes up like normal and I can do anything I want. So partial success!

When I chose Ubuntu, I get the following error message and need to know how to fix:

Windows failed to start and you must either:

1. Install Windows install disk
2. Choose your language
3. Click repair

File:\NST\AutoNeoGrub0.mbr
Status: 0Xc0000098

Selected entry could not be loaded because the application is missing or corrupt

So, thoughts on how to get Ubuntu to launch when I chose? Know there is something I am missing.......

---

### Post by oldfred on 2013-02-23
A few users here that are primarily Windows users do use EasyBCD, but that is a Windows boot loader that uses the old grub4dos (based on grub legacy) to chain load to an install of grub somewhere else on you system.
Windows is not designed to boot anything but Windows.

We normally use grub2 to boot both systems. It is designed to multi-boot many systems.

       [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

    
       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2

---

### Post by c5vetter on 2013-02-23
Guess, I am confused as to what I need to do next to make Ubuntu able to launch like Windows does.

Looks like when I start Ubuntu it fails because it is looking for the following file:

\nst\autoneogrub0.mbr

So, guess I am stuck on how I correct this????

---

### Post by oldfred on 2013-02-23
That is a EasyBCD file that you create. If you really want Easy then you have to go to their forums. Especially with Windows 8 as almost no one has use Easy with UEFI. They just fixed it to work with UEFI recently.

---

