---
title: "Howto: Multiboot Windows XP, Windows Vista, Ubuntu 6.06, etc"
date: 2006-09-19
forum: Outdated Tutorials &amp; Tips
---

### Post by 3370318 on 2006-09-19
There does not seem to be a very good (or at least very accessible) discussion on how to independently (by this I mean not simply chaining boot loaders) multiboot Windows XP, Windows Vista RC1, Ubuntu, and other distros. As such, I would like to share my method for accomplishing such a setup.

My setup uses multiple partitions on a single hd as follows:
Boot Manager – XOSL (on a dedicated partition)
[INDENT]Windows XP
    Windows Vista RC1
    PC-BSD
    Ubuntu 6.06
[/INDENT]
I chose XOSL because it is very convenient to reload from a dedicated partition, it doesn't mess up the MBR, and it looks snazzy. However, getting Vista to work with XOSL, Linux, and Windows XP is surprisingly difficult and requires several steps.

Recommended:
Download and burn a copy of the “Ultimate Boot CD” from [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) as it has a ton of useful tools for partitioning, booting, and diagnostics in a very convenient package. All of the packages that I used (for example, Ranish Partition Manager and XOSL) are all on this CD.

Step 1:
Partition your HD with whatever partitions will be needed prior to installing Vista. I found that Ranish Partition Manager is a wonderful tool this purpose; however, it is text-based.

Step 2:
Install Windows XP (if you don't have it yet)

Step 3:
After Windows XP is installed and configured, reboot and use Ranish to set Vista's partition as active (B for boot in Ranish). I would discourage trying to set the partition active through Windows (setting it active through Windows destroyed my extended partition for that HD).

IMPORTANT:
This step is very important as Vista will otherwise modify the contents of whichever partition is set active; most of the time, this seems to be the partition belonging to Windows XP. If this situation occurs, Vista will store bootmgr and BCD (two all important files without which Vista cannot boot) on the Windows XP partition, NOT on the Vista partition. In this case, Vista will be incapable of directly booting through any other means (not through XOSL, not through GRUB, not through ANYTHING). At this point, Vista is irrevocably tied to the XP partition which cannot change in a manner that would alter the loading of bootmgr. Also, if Vista's boot sequence is altered even slightly (say by installing XOSL) Vista will probably fail to load correctly as will other detected Windows (aka Windows XP) installations. If you choose to run fixboot from the Windows XP recovery, then Vista will no longer load bootmgr and will no longer boot (at this point there is no way to repair Vista). This situation should be avoided.

Step 4:
Install Vista. At this point, you'll need to select a partition to format with Vista's implementation of NTFS. Note that this is a newer NTFS version and cannot be correctly resized with standard Windows tools or other tools such as qtparted.

Step 5:
Install XOSL or whichever boot loader you prefer. If you are unable to install XOSL through UBCD, try saving the files on a FAT32 drive and run the installation from there. I have found that storing XOSL on its own partition saves headaches later on.

Step 6:
Set up XOSL to list Windows XP as one choice and Windows Vista as another. At this point Windows XP will probably load correctly through XOSL, but Vista will not.

Step 7 (Repair Windows XP if it doesn't load through XOSL):
At this point, Windows XP and Vista may not load correctly. To fix the problem with XP, use XP's installation disk to get into the recovery console. Once the recovery console is available, run fixboot (do not run fixmbr as this will overwrite the link to XOSL) and be sure to specify the drive that XP is on (probably C). Vista's drive should also be listed among possible choices, but it will probably some higher letter (like G).

Step 8 (Repair Vista):
Use Vista's installation disk and choose the repair option. It will probably detect that something is wrong, attempt to automatically repair itself, and then ask if you would like to reboot. Do not choose to reboot (the automatic repair doesn't really work). Instead, continue on to the next repair screen and choose the option to repair Vista. If you observe the log file from the repair, it should note that it edited the booting options (toward the end of the log file) and will probably mention BCD. At this point, you should be able to reboot.

Step 9:
Verify that you can indeed boot into both XP and Vista through XOSL without going through any additional boot managers.

As an aside, Vista may boot correctly, but may fail when it actually tries to display the user login (perhaps it assigns a refresh rate out of the range of your monitor). If this is the case, you can press F8 whenever you first boot Vista from XOSL for more options (such as 640x480 resolution) which may be helpful for resolving such errors. Once everything is correctly working, install Linux.

Step 10:
Install Ubuntu onto whichever partition you prefer (note the partition that you choose to format and mount as /). Go through the typical installation procedure until you reach the point of installing the boot manager (grub). Instead of installing to the MBR, choose to install grub onto the root partition (/dev/hd*whatever you decided to format as /*). For example, I installed grub on /dev/hda6, the same as my root partition for Ubuntu.

Step 11:
Set up XOSL to list Ubuntu as another choice.

Step 12:
Install any other OSes you want using the same method as Ubuntu if they are *nix based.

If everything worked correctly, you should be able to boot Windows XP, Windows Vista RC1, Ubuntu, and anything else directly through XOSL without any difficulty.

Note: You could choose to install XP, then Vista (ignoring Step 3), then Ubuntu and install grub onto the MBR. This setup works, but in order to use XP, you must first choose “Windows XP Professional” through grub and then choose “Legacy Operating System” through Vista's boot manager. Also, as noted in Step 3, any change to the booting method on the XP partition will destroy your capability to boot Vista.

Hopefully this will save somebody some headaches and time.

---

### Post by vjones777 on 2007-02-19
Thanks so much for that.  A great howto.  I was actually looking for a howto on getting multiple Ubuntu installations to work (I'd read some discussions that different linux distros don't live together too well on the same hard drive).  Nice to know I can do it ok.

I appreciate that you wrote the guide using XOSL - I've been using it for a few years to multi-boot mutiple Win98s, XP and linux.  I never really understood why GRUB is so popular with all the faffing about on the command line/config files that it requires, when XOSL will do (as far as I know) everything that GRUB does and with a nice graphical interface to boot (groan) which is really easy to use.

Incidently, a really nice guide on multi-booting can be found at [Dan Goodells site]("http://www.goodells.net/multiboot/index.htm").  It even goes into being able to, reliably, boot Win98 from extended partitions, which conventional wisdom says can't be done.  It also gives a good coverage of XOSL.

Thanks again. =D>

---

### Post by brit0n on 2007-03-20
> **3370318 said:**
> 
Step 10:
Install Ubuntu onto whichever partition you prefer (note the partition that you choose to format and mount as /). Go through the typical installation procedure until you reach the point of installing the boot manager (grub). Instead of installing to the MBR, choose to install grub onto the root partition (/dev/hd*whatever you decided to format as /*). For example, I installed grub on /dev/hda6, the same as my root partition for Ubuntu.


Thanks for that. I wish I had read that BEFORE I installed Ubuntu. The other steps were not the problem - THIS one is. I even moved WinXP in a weird move and got everything including Vista working. But my old Linux is more reminiscent of DOS before Windows so I am definitely a newbie to all these graphical interfaces.

So here was the problem....

Installed everything else leaving a 60GB+ unallocated space on a disk which already has 3 primary operating systems booting from XOSL. On another disk, I have a DOS bootable partition - XOSL is on that and I manually edit partition tables and manually restore XOSL so I don't worry when an install smashes my boot loader because I get it back before I do anything else.

After the install, the Ubuntu CD installer wouldn't shut down - no idea what that is about and would frighten off any non-technical first-time Ubuntu user!

Forced a cold reboot and booted into Grub which offered me my DOS boot (and some of the Windows ones). But it wouldn't allow the DOS boot and I had trouble getting it to boot from CD to DOS. Once I fixed that the sledgehammer way, I booted to DOS from CD and restored my xosl and its settings.

Rebooted to hard disk, chose the DOS boot and inspected partition from RPM. Ubuntu (Gparted presumably) had set up two logical partitions. Now I know that Linux now likes to have an ext3 and a swap, but with XOSL it doesn't actually need logical partitions, but maybe that isn't a problem - or is it? Personally, I never use them for boots because XOSL remembers all the primary partitions even if they aren't on the MBR list of 4 (and both WinXP and Vista ignore any attempts at NOT showing the partitions which aren't on there and allow them to be viewed as well).

So of course, I point an option in XOSL at the ext3 partition and it won't boot. Now I know I could create another option in my DOS config.sys boot menu to do a loadlin boot, but doesn't Ubuntu linux boot from it's ext3 partition? Or is this because it made it logical instead of primary?

Ubuntu installer insisted on using Grub (shame on you!) and gave no options to use an existing boot loader or not to use a loader at all which would have been the easiest way for this setup.

So what am I missing? Ubuntu appears to be doing what we all complain about Windows (all varieties) doing - not allowing choice! From your post: *until you reach the point of installing the boot manager (grub)* isn't much use. I don't know if you are referring to an earlier installer, but the one I just downloaded for 6.10 doesn't have any stages so there isn't one where it installs Grub (it does the entire install without asking any more questions after those ones about name, language, keyboard etc at the start which is good installer practice). It certainly didn't ask me to choose options like NOT having Grub or where to put it if I did want it. I thought Grub (and Lilo) are only required for Linux if you wanted to multi-boot and don't have a boot loader already, but maybe things have changed since I read this up. Can't I just BOOT Ubuntu Linux? If I installed it on a clean, brand new PC, would it STILL insist on installing Grub?

Have I missed something about the Ubuntu 6.10 installer? Should I be running it from the CD using some kind of command prompt? How do I get it to avoid GRUB which is DEFINITELY surplus to requirements!

I don't want to do another installation until I know - this is one slow installation compared to Vista for instance (4 times as long but without the reboot).

Any help gratefully received (and meanwhile I'll search on).

Oh and any ideas why the Ubuntu CD installation would refuse to shutdown/restart? If there is a message other than the ubuntu logo and a small piece of orangey-brown bar below it when it stops forever, I can't see it on that dark screen.

Hmmm! I re-read that and I am still a little in the dark about something. You mention *choose to install grub onto the root partition (/dev/hd*whatever you decided to format as /*). For example, I installed grub on /dev/hda6, the same as my root partition for Ubuntu*

Root partition? Each of my partitions has a root. But a root partition?

C:\ is the root of partition labelled C:

F:\ is the root of a partition labelled F:

Did we change the world or is that simply a loose syntax you are using? What is a root partition and does IT have a root? Do you mean the MBR or the Partition Table which take the space which MIGHT under some other system be used by a partition?

I read like heck and I manually write my partition tables and manually restor a loader and it's option files. I boot LiveCD's from DOS partitions on USB sticks. But I chose Ubuntu as a seemingly easy way to install a full distribution of Linux without having to work too hard provided I made way too much space on the disks for it and had a boot loader to keep it separate from Windows.

Did we re-write the technical language in order to keep DOS and Windows programmers out? Hmmm! lol

---

### Post by ammatos on 2007-03-29
I'm half asleep, but...

<A> Think of the "/root" in Linux as the "My Computer" in Windows, not as a root directory in a HD partition.

<B>  You are using the LiveCD disc (which is Windows with the install '.inf' file option in use), in order for YOU to have options you need the ALTERNATIVE install cd (or .iso).  Go to this page, [http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors), pick a site; follow the 'rope', when you get to the proper page - SCROLL DOWN - you should see something like this:

MD5SUMS                                   26-Oct-2006 05:36  645   
 
MD5SUMS.gpg                               26-Oct-2006 05:36  189   

 ubuntu-6.10-alternate-amd64.iso           25-Oct-2006 09:55  695M  Alternate install CD for 64-bit PC (AMD64) computers (standard download)
 
ubuntu-6.10-alternate-amd64.iso.torrent   26-Oct-2006 04:29   27K  Alternate install CD for 64-bit PC (AMD64) computers (BitTorrent download)

 ubuntu-6.10-alternate-amd64.jigdo         26-Oct-2006 04:28  137K  Alternate install CD for 64-bit PC (AMD64) computers (jigdo download)

 ubuntu-6.10-alternate-amd64.list          25-Oct-2006 09:55   98K  Alternate install CD for 64-bit PC (AMD64) computers (file listing)

 ubuntu-6.10-alternate-amd64.template      25-Oct-2006 09:55  1.7M  Alternate install CD for 64-bit PC (AMD64) computers (jigdo template)

 ubuntu-6.10-alternate-i386.iso            25-Oct-2006 09:56  697M  Alternate install CD for PC (Intel x86) computers (standard download)

 ubuntu-6.10-alternate-i386.iso.torrent    26-Oct-2006 04:29   27K  Alternate install CD for PC (Intel x86) computers (BitTorrent download)

 ubuntu-6.10-alternate-i386.jigdo          26-Oct-2006 04:28  135K  Alternate install CD for PC (Intel x86) computers (jigdo download)

 ubuntu-6.10-alternate-i386.list           25-Oct-2006 09:56   96K  Alternate install CD for PC (Intel x86) computers (file listing)

 ubuntu-6.10-alternate-i386.template       25-Oct-2006 09:56  1.7M  Alternate install CD for PC (Intel x86) computers (jigdo template)

 ubuntu-6.10-alternate-powerpc.iso         25-Oct-2006 10:00  698M  Alternate install CD for Mac (PowerPC) and IBM-PPC (POWER5) computers (standard download)

 ubuntu-6.10-alternate-powerpc.iso.torrent 26-Oct-2006 04:29   28K  Alternate install CD for Mac (PowerPC) and IBM-PPC (POWER5) computers (BitTorrent download)

.............................................................................ETC, ETC, ETC, ETC.

You should note the magic word 'alternate', as in "ubuntu-6.10-alternate-powerpc.iso";  find the alternate .iso that fits your toy, DL, Burn.  This install will give you a DiskPartition tool and allow you to pick LILO or GRUB; though I'm sure at this stage you should be able to insert your beloved XOSL.

<C>  Please, for those that haven't visited the "Understanding MultiBooting and Booting Windows from an Extended Partition by Dan Goodell" site @ [http://www.goodells.net/multiboot/index.htm](http://www.goodells.net/multiboot/index.htm).  PLEASE do yourself a big favor and visit this MOST excellent site.  There is more info here than meet the eye, every single link on this site opens a new door.  For those considering GRUB vs. LILO vs. XOSL (etc.) - please see the "Miscellaneous Notes" link at the bottom of the MAIN page.  Also note that the other three links at the bottom of the page: "Acknowledgements", "Links to More Information", and "Appendix: An Introduction to Virtual PC®" - are also full of excellent information.  They all add tons of info that anyone concerned with Multi-Booting various OPs has to see. a PRIME and PREMIER site.

Just as a note, you should remember that YOU are asking for help, I don't think anyone is trying to shove GRUB down your throat, so may I suggest that you filter "the attitude" that comes across in your responses;  it one of the reasons - 'helpers' stop helping.  I speak from a platform of age - as I've been a 'helper' since Sinclair (Timex), Commodore & Atari were hooking into CompuSrerve @ 300 buad.  Maybe I'm being a little OVER sensitive (or over protective), but over the years I've seen lots of good folks stop helping - because they get pissed at folk's attitude, and if there is one arena where we can't afford to turn ANYONE off, it in the LINUX (ALL OF THEM) arenas.  If I misread your vibe -  sorry, but it is coming across.

Hope this post help with your problem;  be good, be nice, and enjoy!

angel

---

### Post by Remco on 2007-05-04
The root partition is the partition that has Ubuntu's root-directory (/). In the non-Windows world, partitions don't have letters. Each partition has a filesystem, and that filesystem can either be mounted as "/", or in a subdirectory of "/". This for example allows you to use different partitions for "/home" and the rest of the directory tree.

---

### Post by kahurangikea on 2008-04-29
It is also important when installing XP to keep the partition in the same place in partition table as when first installing.

---

### Post by sbooder on 2008-06-18
Hi all,
                I been registered here for a while but only just got round to finding time to multiboot Ubuntu on to my new PC.
I have a Dell Inspiron 530, 2GHz Dual Core 2GB RAM and a 300GB HD.  I have already set up a Vista, XP dual boot using this tutorial ([http://www.syschat.com/dual-boot-vista-xp-vista-already-1946.html](http://www.syschat.com/dual-boot-vista-xp-vista-already-1946.html).

I now want to add Ubuntu to the fray, and wondered if following the steps in this thread would be a wise move or not, with the following being the last step I took setting up the dual boot Vista XP:
bcdedit –set {ntldr} device partition=C:
bcdedit –set {ntldr} path \ntldr
bcdedit –displayorder {ntldr} –addlast 
bcdedit -set {ntldr} description "Microsoft Windows XP"

Also can I load XOSL in vista on NTFS or is it always preferable to shrink the Vista drive to create a separate drive for XOSL?

Thanks for any help.
Simon.

---

