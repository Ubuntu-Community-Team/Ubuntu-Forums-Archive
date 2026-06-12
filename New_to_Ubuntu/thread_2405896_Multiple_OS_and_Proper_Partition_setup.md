---
title: "Multiple OS and Proper Partition setup"
date: 2018-11-12
forum: New to Ubuntu
---

### Post by hennmann on 2018-11-12
I'm new to Ubuntu and still learning and have gotten farther than I ever have with help from this forum.
This all started with my older hardware which possibly would have driver issues with the latest OS and earlier hardware. I started with a clean install with just the Ubuntu 18.4 just for this reason after all dealing with multiple OS would complicate things as it is.


First of all here is my hardware
Computer#1 Running Win7/64 Pro/Ubuntu 18.04
Gigabyte GA-M68MT-S2 Rev1.3 AM3 (BIOS Boot)
Athlon II 640x4 CPU
Gigabyte Geforce Silent Low Pro GT1030 2GB
16 GB Kingston HyperX Fury 16GB 1600
WD 160GB HHD


I started on this setup to test multiple OS and also to see what possible issues with drivers etc. I would have which required installing the proper driver performing all updates etc. and it works great with Ubuntu 18.04 so I did a clean install of Win7/64 Pro and rebooted with a flash drive, selected install, something else, and used the Ubuntu partitioning tool to resize this scrawny little drive into 2 partitions of equal size. After the partitioning was done and was very straight forward just clicking on the one partition and shrinking it. After this I letterip and installed or should I say let Ubuntu install itself. The Grub boot loader works great, cleared up minor driver issues, and performed a complete update process. Both Windows and Ubuntu work flawlessly as is. Now I moved to my second computer to attempt the same thing. One thing I might add at this point is for my Gigabyte with BIOS boot and no UEFI  the partitioning tool on the same Ubuntu was basically click on the partition and click on an arrow and watch the partition shrink or enlarge to determine the size of unallocated space. Very simple considering Windows was already installed and then after this space was created select install. Oh and also I used Ubuntu to resize the partitions before I read on this forum it was recommended to use Disk management but I had zero issues using Ubuntu (on both computers). 


Computer#2 Ran Ubuntu 18.04 1st, worked great "right out of the box" with zero issues, now a clean install of Win7/64 Pro
MSI 970A SLI Krait Edition AM3+ (UEFI Boot)
AMD FX8370 X8 CPU
16GB Kingston HyperX Fury 1600 RAM
MSI Armor RX570 OC Edition
WD 1TB WDS1 00T2B0A-00SMS0 Blue 3D NAND SSD

As mentioned before from past experience I did a complete clean installation of Windows first to prevent Windows from molesting a Ubuntu installation and the only other differences other than hardware being 5 years newer AND UEFI instead of BIOS boot and a solid state drive thrown into the picture as well.

 I booted off the flash drive, selected "install" instead of "live", and when I reached the point of where to install and preparation I selected "something else" to give me more options such as multiple OS on one drive etc.
The partitioning wasn't as simple and straight forward as on computer #1, the Gigabyte but I resized the single 1TB partition recognized as 931.39 GB on Computer Management to a selection of 500 GB and Disk management now recognizes my Windows partition as 465.66 GB with Windows still functioning after my attempt of installing Ubuntu except with this now resized home for Windows just like computer #1. 

Now back to the attempt on the Krait, on the Gig I made 2 partitions out of 1 and selected install and let Ubuntu do it's thing but doing the same thing on the Krait I got the nag "no / directory" so I created one, created a /swap, /boot, /home,/tmp after correcting or should I say attempting to, then the nag about the boot partition to install the boot loader which I selected my newly created boot partition. At this point I now selected install and updates etc. were downloading and installation was taking place looking normal as well. After a number of minutes I get a boot partition error and continuing installation discontinued. This is where I stopped, rebooted to see what is left of Windows and it is running fine where I type this post.

Now instead of trying again not really knowing what I'm doing please provide me with the PROPER setup of all partitions like "the good old days" when I first tried various flavors and one had to set up all partitions first and then install. Keep in mind back then I didn't know how to run multiple OS on one hard drive and use a boot loader for multiple OS so I got by by running multiple hard drives and just pressed F11 to enter the boot selection at first time boot before the OS was being looked for.

I do not and never did like putting everything in one partition in case the OS had to be reinstalled and keep important items in different partitions and hard drives in case of an OS failure.
Also one mistake I did this time is I used the size of RAM as a size determination for my swap partition and due to the size of the hardware on both PC's this is totally unnecessary as 2 GB is recommended for what I have. 
I would  like to set up:
/boot
/swap
/
/home
/tmp
and whatever suggested partitions are recommended like the "good ol days"
I have lots of room so space is not a concern including a 3TB Seagate for storage and perhaps Win10

Have pity on this poor NOOB slob and keep the info NOOB friendly as I can do all of this in careful steps making sure things are properly set up FIRST instead of having garbage set up and limping along! Also setting things up a bit better is a bit more complicated instead of the simple bing bang boom single partition method but I look at this as a learning process like I did years ago just setting up a computer from a pile of parts and installing Windows from scratch. Also I see the partitions need to be "mounted" and I'm slowly learning this as well and perhaps this was the boot partition error or maybe I was supposed to use the Windows partition to install the boot partition and Grub bootloader? Oh the joys of letting an OS do everything during installation instead of doing it carefully from scratch as this forces one to learn how to do it properly (I hope) 

One more question before I forget is Install immediately or install while running in "live", which is better?

After I posted this I noticed one thread about partitions and errors was moved to Installation and Upgrading so please move if this needs to be done

---

### Post by oldfred on 2018-11-13
If you are using a 3TB drive then you have to have gpt partitioning.
Windows only installs to gpt drive with UEFI.

You can run in live mode as much as you want, it just is a bit slower reading from flash drive. But once in RAM it is just as fast. 

Standard desktops do not need separate /boot and installer now uses a swap file, but will use a swap partition if found. 
Since more than one operating system you may want a shared data partition. But Windows fast start up will set hibernation flag on all NTFS partitions. And the Linux NTFS driver will not mount read/write hibernated NTFS.

Do not know about MSI motherboards with AMD chips. Otherbrands have needed IOMMU settings changed in UEFI and boot parameters for iommu.
       GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0 uses this boot parameter: amd_iommu=on iommu=pt  & UEFI settings
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

---

### Post by hennmann on 2018-11-16
Thanks oldfred
I have the 3TB taken out of the picture as to not complicate things and I used the portioning tool to break up into smaller when I first installed. 
I will read all of this and keep in mind this MSI works flawlessly with either or and when I first set it up I placed Ubuntu only on the SSD. The Gig only had issues with the Video but this has been cleaned up. In a case like the MSI and UEFI would I be better off to have two separate drives or partitioning the newly created space is not that bad? Years ago there was considerably more mention of partitioning and setting up the drives first prior to installation. Using the software to automatically install is perhaps just making those getting into this OS understand less IMHO. Partitioning shouldn't be that big of a deal, it's the damn CLI that gets me and if you don't know the commands you are simply out of luck until you find or somebody posts.

---

### Post by hennmann on 2018-11-16
Oldfred after glancing around on the links you provided they have a whole slew of other problems thrown into the pictures just plain and simply complicating the situation. As mentioned first this board WORKS perfectly  with only one OS on it including Ubuntu. It boots fast works stable and smoothly and shuts down within only a few seconds. 
Proper partitioning and mounting of the partitions and then setting up the bootloader. NO I DONT want everything on a single partition for Ubuntu. To me this just doesn't make any sense if anything should go wrong.

---

### Post by mastablasta on 2018-11-16
what would you need multiple OS on "bare metal"? you can just use virtualization (e.g. Virtualbox) for that. i run xubuntu, a security oriented OS, 3 separate test servers and a centos based server all from a single core windows XP machine via virtualbox. at one point i had about a dozen of different OS, but those i was not impressed with or not used much got removed. now it's mostly just servers for testing purpose. my PC is old, but new ones can run various linux OS (even those that need more resources and windows). the only need for bare metal install are GPU drivers (e.g. gaming needs GPU acceleration and often windows) or if you need a specific OS to do some heavy computing. but for that a separate machine might make more sense. 

aside from the fact that you can access another OS really fast, it is also safe. you can make a snapshot, mess up the OS completely so nothing works, then you can restore form snapshot (in my case restore takes about 45 secs but i have old PC).

---

### Post by hennmann on 2018-11-16
Bare Metal? Sorry that I don't understand but other than that:
One computer, one SSD with two OS. Windows on half and Linux on the other half like my Gig with BIOS boot except this Krait addition with SLI970 is UEFI. 
Like the "Good ol days" a proper partition setup instead of "one kettle of fish" with all my fish swimming in the boiling water. 
Top this all off with the Grub bootloader showing a menue with all my options in dazzling purple/burgundy graphics as well I might add. The Krait with the FX8370 is fairly substantial to say the least so I will read the NOOB manual. Thanks for the link!
BTW I have older hardware with small CPU, RAM, (P4&128 megs of RAM)and the "live" version sucked the "big one" because the entire OS had to run within the spec of RAM. A 3GB swap and Puppy 4.3 and this iddy bitty 2002 HP OmniBook soared like an eagle when installed on a snail 5400 RPM HHD.

---

### Post by oldfred on 2018-11-16
Windows in UEFI boot mode wants multiple partitions:
       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

Ubuntu's default install is / (root) only. But with UEFI it will add or use an existing ESP - efi system partition (FAT32).
And now it uses swap file, not swap partition.

If you want data separate having a separate /home is the easiest alternative, but you have to use Something Else. You can create partitions during install into unallocated space, but I normally use gparted and create them in advance. You still have to use Something else to tell install which partition to use (change button).

Bit more advanced is separate data partition(s). But you have have to add mount to fstab, set ownership & permissions (unless NTFS). NTFS permissions are set in mount only.  Some like to separate Music and/or video or other larger data partitions. You can choose what you want, but having too many small partitions makes it difficult to manage available unused space, so some trade offs.

---

### Post by hennmann on 2018-11-16
Thanks again
When the installation "went south" all the created partitions remained with the new resized Windows partition (including system partitions created by Windows) and Win 7/64 Pro is booting, functioning, etc. like nothing was ever changed. The partitioning tool within the Ubuntu installation when selecting "something else" actually worked quite well with the exception that I missed or incorrectly completed a step or task. As mentioned earlier one mistake was making the swap too large as per the old rule of thumb of the amount of RAM dictates but this is easy enough to rectify. As for the boot partition perhaps the only mistake was creating and mounting the boot partition leaving the Windows boot sector intact and perhaps this created a conflict. 
Swap partition too large and 
Boot partition error indicated during installation causing installation to be aborted by Ubuntu automatically. This resulted in myself unable to determine what went wrong other than no Grub boot manager installed (maybe? maybe not?) Everything is still there IE all partitions created and whatever has been installed (if anything) on them as Windows doesn't like Linux and won't let me look in there or indicate anything is even there since these are not NTFS partitions. As for the above posted Ubuntu user manual it is very vague just showing how to perform a very basic install fully automated with NO partitioning suggestions. 
Yes too many partitions can be a problem as well but /boot(IF required, /, /home and perhaps /tmp shouldn't be unreasonable. 
As for "live" installation?
It is slower and probably not much better than from scratch like I'm attempting to do? Otherwise perhaps it can be used to diagnose the problem being able to
let me look in the partitions?
As I read your link
LVM or encrypt entire drive was not selected at all. Fast boot is also not enabled and Hibernation is not enabled as well and doesn't even appear in shut down menue for Win7

---

### Post by oldfred on 2018-11-16
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please attach link to the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by C.S.Cameron on 2018-11-17
> **hennmann said:**
> then the nag about the boot partition to install the boot loader which I selected my newly created boot partition

I normally specify the drive for boot loader installation rather than a partition, ie sdx not sdxn.

---

### Post by hennmann on 2018-11-17
> **C.S.Cameron said:**
> I normally specify the drive for boot loader installation rather than a partition, ie sdx not sdxn.
Now while trying to sift through all of this documentation of which I see people wondering if RAID is the problem etc. etc. and I'm wondering are these people just having problems in general even if using ONLY Ubuntu or for dual booting?? Installing Ubuntu by itself on my Krait A970SLI gives absolutely no problems whatsoever including drivers. It shouldn't have to take all of this searching for a solution to a boot loader situation IF their even is one??? Thanks for your suggestion C.S.Cameron and perhaps this is the only problem or just a damn installation glitch making things more complicated than they need be such as wading through all these hyperlink posts. I guess I should speak a different language because nowhere can I find the simple basic instructions on how to properly set up a hard drive from scratch for L I N U X instead of letting software automatically set up a hard drive. I guess we have to automate everything now and let the learning basics fall through the cracks. The links above just show the automated basic steps with very little else. Sorry for my attitude but what steps I had to perform for older versions, which I might add helped the learning process including Mandrake 7.0 and this is going back a long way but being that far back I have forgotten a lot of this. 
BTW this Krait edition board is 2015 and EFI has been around before this so we have had time to hopefully streamline this different BIOS setup. 

Here is another senario?? What is involved to install Linux first, then Windows? Obviously there is nothing wrong with my installation if Ubuntu loves my Krait as is with NO problems

---

### Post by oldfred on 2018-11-17
If you just want Ubuntu in UEFI mode, you only must have two partitions, the ESP - efi system partition and / (root). Everything else is optional and up to you if you want more. You do not need swap now since swap file is used not swap partition. Many like separate /home or data partition(s). Or other partitions for other uses.
Windows has its own requirement as posted above for multiple partitions.

       [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by hennmann on 2018-11-17
Before your latest post I looked in my so called BIOS or UEFI or Mainboard settings and Quick Boot is not enabled, with no HHD security etc. and remember I'm somewhat blindly stabbing around in the dark.
One thing while poking around in there is a setting for UEFI. It gives the option of "FULL UEFI" or "LEGACY and UEFI" which the help on the side mentions this is for OS that are the conventional BIOS BOOT AND Newer UEFI software such as this Ubuntu and since Win 7/64 is a bit "dated" I selected the later of the two choices. I went through the motions of reinstalling and Ubuntu acknowledges 18.04.1 is there and installed asking if I want to install beside or erase and I selected something else again clicked on each partition created earlier to make sure they are mounted etc. and when I selected install now, it indicated Swap was going to be formatted which it did. No errors reported and a full installation was performed and at the end instructed me to restart the computer for installation to be completed. After reboot there was no boot loader and the system went directly to Win7 as usual. I rebooted to the flash drive, selected something else and this time went through the same motions BUT selected formatting when I selected each partition. The only partition that couldnt be formatted was the dedicated BOOT BIOS and this concerned me that it was labeled BOOT BIOS?? 

AS for the location of Boot manager I wasn't given the option of selecting this so called Boot partition (all partitions excluding the BOOT BIOS) so I elected to select the / partition as it was one of the choices for the Boot Manager.  Installation continued again smoothly but again when restarted there was NO GRUB boot manager and again the computer went on it's merry way to Windows.

Am I selecting the wrong Partition for Grub?
Do I need to delete the Boot Partition?



Otherwise I have:
 Dedicated or Reserved BIOS BOOT
/
Swap  (Still large based on RAM but this is for another day)
/Home
/Tmp

Since I would have to run "Live" or again attempt to reinstall I'm typing this on Windows OS.

As per:
[https://ubuntuforums.org/showthread.php?t=2406150&page=2&p=13817025&posted=1#post13817025](https://ubuntuforums.org/showthread.php?t=2406150&page=2&p=13817025&posted=1#post13817025)

I even asked the question there
Why is GParted always recommended instead of using the partitioning tool from Ubuntu?? I'm always using the partitioning tool after selecting "something else"
If the "Something Else" partitioning tool isn't recommended, why is it there in the first place?

---

### Post by hennmann on 2018-11-17
> **oldfred said:**
> If you just want Ubuntu in UEFI mode, you only must have two partitions, the ESP - efi system partition and / (root). Everything else is optional and up to you if you want more. You do not need swap now since swap file is used not swap partition. Many like separate /home or data partition(s). Or other partitions for other uses.
Windows has its own requirement as posted above for multiple partitions.

       [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

As per the link you posted they highly recommend a Swap (from what I gathered)

I have lots of RAM and a reasonably sized CPU so?
Should I scrap the Swap and Boot partitions or should I just eliminate the mystery BOOT BIOS partition and leave the swap?
Do I dare select my Windows Partion for the BOOT Loader location?

---

### Post by wildmanne39 on 2018-11-17
> As per the link you posted they highly recommend a Swap (from what I gathered)
That was years ago when computers did not have much ram and ubuntu still used a swap partition, if you are running a recent version of ubuntu, as oldfred said swap files are now used instead of swap partitions, so they are no longer needed, my computer never uses the swap file either since I have enough ram.

---

### Post by hennmann on 2018-11-17
So get rid of it and what about the boot?
Right now I'm running live so I guess I can stumble on with the partitions and Bootloader.
Also use the Ubuntu Partitioning tool or GParted? I would have to store to a flash drive or attempt to run in live

---

### Post by Geoffrey_Arndt on 2018-11-17
Gparted is recommended from the "Live Mode" of the installer iso OR a Live DVD/usb flash-stick of ANY Linux distro.   The reason is because the "bare metal" (the physical hardware drives of the PC) should be unmounted prior to partitioning operations.

---

### Post by Geoffrey_Arndt on 2018-11-17
Also, I kindly suggest you just use the standard installer designed layout for the install - - which is just the root partition and a swap file.   So, on a standard install on UEFI - - if you have more than TWO partitions, you have too many.   And that complicates things greatly.    

And you don't even need GRUB if you do the standard UEFI install on a Windows 10 machine because the installer will use the Windows boot loader to load both Windows and Ubuntu (per your choice).   So, I can't recall if Windows 7 is slightly different.

EDITED:

2nd Best (and easiest option) is to install Linux on an external separate usbv3 SSD - - and not the old, complex dual-boot scenario of the "good old daze."

pls see:   [http://omahatechconnect.org/2016/07/04/sandisk-extreme-500-portable-ssd/](http://omahatechconnect.org/2016/07/04/sandisk-extreme-500-portable-ssd/)

1st Best (by far) method to run Linux is to get it pre-installed like the System76 Meerkat - - and to keep Windows on it's own hardware and connected via a wireless network or just one of the many cloud options. 

pls see:   [https://system76.com/desktops/meerkat](https://system76.com/desktops/meerkat)

BTW - - Windows generally must be installed first.   Installing after a Linux is already on the machine is way complicated (and above the pay grade for most).

---

### Post by hennmann on 2018-11-17
Installing Windows first was what I always did and I have a second hard drive I could dedicate to Ub but the bootloader? With my current setup what is wrong? Am I selecting the wrong place for the bootloader to be installed? Do I dare select the Win7 partition for the location?

---

### Post by Geoffrey_Arndt on 2018-11-17
Yes. 

   Usually, on a one physical drive system that means "sda" . . . not sda1, sda2, etc.   And certainly not in an unnecessary boot partition or even more useless temp partition.   You can always later (after install) change the disk layout by adding more partitions.    Keep things simple at first. 

  And if your doing a proper UEFI install, the boot loader used is the Windows boot loader (although I've only done a couple UEFI installs - - and just let the installer choose to put it where it actually needs to go).

---

### Post by hennmann on 2018-11-17
As per one website they didnt make a boot partition and installed it on the 130 meg Windows system EFI boot partition. Mine has the identical partition but not labeled the same and I installed it there without a boot loader partition. Ubuntu gave me crap for not having a dedicated boot partition and I installed it anyway! System rebooted without me giving the okay and posting a link to that website!! Anyway system now booted back into Windows like nothing was ever done and NO GRUB bootloader!
It SHOULDN"T have to be this difficult to install multiple OS on a single SSD on a UEFI system!

[https://www.tecmint.com/install-ubuntu-alongside-with-windows/](https://www.tecmint.com/install-ubuntu-alongside-with-windows/)
This is where I installed it with no success

---

### Post by Geoffrey_Arndt on 2018-11-17
Yes, the EFI boot partition is the standard on UEFI.   (but if installing GRUB in legacy mode, it will be sda).    The recommended size for EFI is 500 MB.   The installer iso should be using UEFI mode and not bios/mbr.   IF (repeat IF) you can't get your head into reading the excellent info in OldFreds messages, then another resource is to use Google's Youtube resources (use the inlaid search tool on Youtube home).   Search for "Install Ubuntu Bionic Beaver" on UEFI PC" or something similar.    Then take a couple days to really view several video tutorials.  Some are useless, but others can help.

BTW - - another option is to change UEFI firmware settings to Legacy mode and do the install via that path.   Just be careful that you retain GPT for your drive architecture.  If  using Legacy, no need for EFI partition, just go with the standard /root and a 2-4 GiB swap partition as that still works just fine.  (if your Win7 is UEFI - - then do not use Legacy for Ubuntu).

---

### Post by C.S.Cameron on 2018-11-17
> **hennmann said:**
> Installing Windows first was what I always did and I have a second hard drive I could dedicate to Ub but the bootloader? With my current setup what is wrong? Am I selecting the wrong place for the bootloader to be installed? Do I dare select the Win7 partition for the location?

Have you tried installing the boot loader to the drive and not to one of the partitions?

ie sda not sda1

---

### Post by Geoffrey_Arndt on 2018-11-17
CSC . . . already suggested once . . (?).

But for now, the _best option is to get the "Boot Rescue CD" report as suggested by OldFred_.   That way we can see more of what's actually  going on.    

And finally, yes, UEFI dual-boot installs can be VERY difficult (and others as slick as snail snot) . . . that's why I don't bother with dual boots anymore (even if I were still running Windows, which I'm not).   Even after a successful install, MS Windows updates have been known to render Linux unbootable.

---

### Post by oldfred on 2018-11-17
We are all guessing here what your issues are.
       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please attach link to the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by hennmann on 2018-11-17
As mentioned earlier in this feeble croak for help in my BIOS aaaarrrrrg or whatever it is called IFE Discombobulation I HAVE the OPTION of UEFI and UEFI/Legacy which works for both OS in case I have an older OS that needs it. I kept this enabled because I have Win7/64 and even though this was enabled my Ubuntu 18.0.4 USB Drive which was set up for UEFI booted up and went through the motions quite nicely I might add. Now if you look at the link I posted about the installation of Ubuntu into a UEFI sys, you will notice the Windows Boot at about 130 Megs is labeled Windows Boot EFI. Mine wasn't hmmmmmm? What is going on here? I selected this partition for the Bootloader, again here we go yet again, NOTHING, Nichts, Nada. So okay desperate situations= desperate measures so I enabled UEFI in the BIOS thingy as BIOS is the only terminology I know for this "Pandora's Box" saved and rebooted and Windows is booting up nicely in full UEFI mode so back again here we go with the Ubuntu installation and this time during the partitioning my Windows 130 MEG is now recognized as Windoze BOOT EFI!! This is where I selected the Grub Bootloader to be placed even though out of the blue there is also a 1MEG Grub boot partition that I didn't create within my collection of Ubuntu partitions. I left that one alone as it is only 1 MEG and I treated it like a coiled up Rattle Snake or should I say very venomous Krait (that my motherboard, Krait Edition is) that makes a Rattle Snake look like a Quire Boy. All the partitions were formatted remounted and left alone (yes all of them) and then I selected "Install" with no nags, hisses, or Snake bites.
The system did its installation "thang" rebooted and I was greeted with the Burgundy/Purple Boot Menu like on my older Gigabyte board and am now typing this on Ubuntu dual booted with Win 7/64 on a 1TB SSD.
Yes this BIOS or whatever you call it has full UEFI and also allows both Legacy/UEFI to function in harmony but with this enabled causes a little glitch with the bootloader and believe me I put that Grub in many different places with nothing happening.
A very simple problem causing a big headache and being such a small problem causes probably a number of us to explore many other possibilities when not needed. This should be mentioned more when one keeps ending up in Windows.

---

### Post by hennmann on 2018-11-17
And yes everybody thanks for your help!
Now I guess while I'm at it I might as well go back to an earlier thread about driver issues and get the command for a full system update since this is a fresh install of an early version of 18.04

---

### Post by C.S.Cameron on 2018-11-18
[QUOTE=Geoffrey_Arndt;13817064]CSC . . . already suggested once . . (?).
/QUOTE]

Twice, my post #10 and your post #20.

Just not sure if OP was listening.

---

### Post by C.S.Cameron on 2018-11-19
Speaking of Kraits, the wife says she spotted one in the garden this morning.

---

