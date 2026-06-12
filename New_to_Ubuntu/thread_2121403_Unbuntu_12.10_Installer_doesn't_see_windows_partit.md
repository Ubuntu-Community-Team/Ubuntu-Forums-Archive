---
title: "Unbuntu 12.10 Installer doesn't see windows partition."
date: 2013-03-01
forum: New to Ubuntu
---

### Post by BlackTai on 2013-03-01
Okay, first off I'm brand spankin' new to Linux.  I only know what I've figured out out from the live USB.

I want to install ubuntu 12.10 side by side with windows but from the live USB the option isn't there, it tells me I do not have any OS installed on it.  I came across [this post]("http://ubuntuforums.org/showthread.php?t=1987011") which sounded a lot like my issue.  I have a motherboard with UEFI and I reused my old HDD for this build.  I kinda remember that windows yelled at me about needing gpt on UEFI and I think I let the windows installer format the whole drive.  oldfred from that post informed that user to use FixParts.  So I tried to do the same.

One Problem.  [The FixParts Tutorial]("http://www.rodsbooks.com/fixparts/") doesn't make any sense to me.  I want to use it from windows, and I get this far... 
[IMG]http://imgur.com/bjVwguK[/IMG][http://imgur.com/bjVwguK](http://imgur.com/bjVwguK)

Can someone please assist me?

Thanks!

---

### Post by oldfred on 2013-03-02
We need to confirm how you installed Windows. If drive was gpt and you installed Windows in BIOS/MBR mode then you do need fixparts to removed the backup gpt partition table as Windows leaves that.

This only works on MBR drives:
sudo fdisk /dev/sda    

       sudo parted /dev/sda unit s print

If drive is gpt not part MBR part gpt, fixparts just exits. You can from the Ubuntu liveCD download gdisk which is the fdisk for gpt drives.

---

### Post by BlackTai on 2013-03-02
Okay, you need to confirm how I installed windows.  Windows 7 was installed on my HDD with an old motherboard.  When I built my new machine, I upgraded to an ASUS Crosshair V motherboard, which has UEFI on it.  Windows would not load, so I then re-installed Windows 7 64bit.  It automatically formatted the drive.  And now it works.  If you need different information, I'd be happy to follow any instructions.

However, I will need more basic instructions than this:
> [COLOR=#000000]This only works on MBR drives:[/COLOR]
[COLOR=#000000]sudo fdisk /dev/sda [/COLOR]

[COLOR=#000000]sudo parted /dev/sda unit s print[/COLOR]

[COLOR=#000000]I assume that you are informing me that I'll need to type the command "sudo fdisk /dev/sda" somewhere...  But where do I do that?  I'll gather you want me to load up my liveUSB.  But from the desktop where do I go and what do I type to get there?[/COLOR]

[COLOR=#000000]I apologize if my lack of understanding is frustrating, thank you for your patience.[/COLOR]

---

### Post by BlackTai on 2013-03-03
Okay... I found the terminal and now have a basic understanding of it... 

```
ubuntu@ubuntu:~$ sudo fixparts /dev/sda
FixParts 0.8.4

Loading MBR data from /dev/sda

This disk appears to be a GPT disk. Use GNU Parted or GPT fdisk on it!
Exiting!

ubuntu@ubuntu:~$
```

```
ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Model: ATA WDC WD1600AAJS-0 (scsi)
Disk /dev/sda: 312581808s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start    End         Size        File system  Name                          Flags
 1      2048s    206847s     204800s     fat32        EFI system partition          boot
 2      206848s  468991s     262144s                  Microsoft reserved partition  msftres
 3      468992s  312580095s  312111104s  ntfs         Basic data partition

ubuntu@ubuntu:~$ 


```

I don't know if this is useful information or not but it's somthing.

---

### Post by oldfred on 2013-03-03
You have Windows in UEFI mode. So you need to boot the Ubuntu install flash drive or live installer in UEFI mode not BIOS mode. From UEFI menu you should get two choices, one UEFI and the other BIOS/Legacy/CSM or whatever your system calls it.

If Windows 7 and not a new system that had Windows 8 pre-installed you do not have to worry about secure boot, but otherwise install is the same.

 
You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

Best to use Windows tools to shrink Windows and reboot Windows a couple of times to get it to run its chkdsk and make other fixes for its new size.
Then backup efi partition and Windows if you have spent a lot of time housecleaning and updating Windows install.

      
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by BlackTai on 2013-03-04
Okay, so I have imaged my C drive, created Repair Disks, used windows to shrink my drive, and booted my FlashDrive with the liveUSB installer on it in UEFI mode.  And I'm still not getting the option to install side by side.

So now what should I do? I've spent all night rechecking my work and I have done everything that was asked.  With one exception, my motherboard does not have a quick boot/fast boot function that I can see, so I wasn't able to turn it off.  Would that prevent me from being able to side by side install, or do I have other problems?

---

### Post by oldfred on 2013-03-04
The issue with fastboot is that some systems only can then get into UEFI from Windows. So if Windows does not boot, then you cannot get into system to fix it.

I only asked for sda, do you have an sdb that is a small SSD? Or an UltraBook which is Intel SRT and uses RAID. Standard desktop installer does not see RAID. Brand of computer does not really matter as Intel SRT is Intel standard.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
      Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)

    Quotes from those who installed.
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

### Post by BlackTai on 2013-03-04
Let's see.  I have an 
ASUS Crosshair V AMD motherboard
AMD FX 8150CPU
8gig 1600 DD3RAM
WD internal HDD 160gb
and a WD MyBook 2tb

I don't have a SSD, no RAID, and I'm not using Intel components.  So I do not think I have Intel SRT.

---

### Post by oldfred on 2013-03-04
If you use gparted from liveCD/DVD/Flash does it show drives. And do any partitions have red or yellow icons next to them indicating issues? Click on icon to see what issue is if you have one.

---

### Post by BlackTai on 2013-03-04
Sorry for the delay...

Yeah I do.  There's a strange 128mib on /dev/sda2 with a flag. [IMG]http://i.imgur.com/Tb0L0Oo.jpg[/IMG]

---

### Post by oldfred on 2013-03-04
That is the ms reserved partition which does not have a format so gparted will not parse it, but it is ok. Windows has to have space to store serial numbers, DRM license info, and some virus checkers may use it.

Are you booting in UEFI mode? Ubuntu should offer just to install to unallocated space or let you manually partition if you want a separate /home.

---

### Post by BlackTai on 2013-03-05
I'm getting this screen when I choose to boot into LiveUSB in UEFI, so I'm pretty sure it's loading in UEFI.
 [IMG]http://pix.toile-libre.org/upload/original/1347445084.png[/IMG]

I choose to try ubuntu and from there I attempt to install.  If I choose "something else" what are the steps I should take to get it to dual boot?

---

### Post by oldfred on 2013-03-05
See post #5.

If you just do the default install it will only give you / (root) and swap. Better to use Something Else or manual install and choose a smaller / of 25GB and separate /home or data partition(s). You then do have to choose partition size, format (ext4), and mount like /, /home or other. You do not need other system partition for most desktop installs, but may want data partitions. If dual booting with Windows also create a shared NTFS data partition. I think the installer now allows that, it did not have the NTFS driver until after the install, so you used to just leave unallocated and create it later (or before hand).

---

### Post by BlackTai on 2013-03-05
K... I am going to want to use my external hard drive for all my stored data so I don't think it will benefit me to separate my root and home.  However, how large should I create my swap?  I have 8gigs of RAM, and [NixiePixel]("https://www.youtube.com/watch?v=GhnLk3gviWY&list=HL1362502398&feature=mh_lolz") says I'll need twice the size of my RAM.  Do I really need 16gigs of space?  And what should happen If I add/upgrade my ram?  

Even so...  before I do this I want to clarify my plan with you.

Run the installer from my LiveUSB.
Choose 'somthing else' when prompted.
Create a logical partition for the swap (however large you think it should be)
Create a primary partition for (/) and use the rest of the space.
Then install ubuntu on (/).

From what you know of my situation.  Do you think this will achieve a dual boot?  Or have I skipped a step?

---

### Post by oldfred on 2013-03-05
I would still create a / (root) of 25GB and separate /home for the rest of the space you want for Ubuntu.

The old rule of 2X RAM was when RAM was only 256K or 512K. Once you get over 2GB you will not use swap much. And with 8GB you may never use swap. You would have to load every program and edit large videos all at the same time to need swap. But if you hibernate then you need to be able to save all of RAM into swap (again only if you have filled RAM) or it needs to be the same size as RAM in GiB not GB.
I suggest 2GB for swap if not hibernating. And with Linux it boots pretty fast so hibernating does not add much.

       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by BlackTai on 2013-03-05
Okay then, that leaves me with a 3gig home folder but oh well.  I'm installing now.  Hope this works! *fingers crossed*

---

### Post by oldfred on 2013-03-05
I might shrink /home a bit and save the space for future use, but that is up to you.

I installed a new 650GB drive several years ago. I put 2 100GB data partitions and have not filled those. I left most of the rest of drive unallocated and started adding 25GB / (root) partitions for testing or betas. I now have too many. :)

---

### Post by BlackTai on 2013-03-05
Well that didn't work mostly.

So no dual boot first off.  Then I tried to get my dual monitors to run which blanked out the screens.  Rebooted and now no desktop or anything.  Sheesh.  I'm thinking reinstall first off...  Then what?

You think I should shrink /home?  3 gigs is pretty small I'd think. but then again I'm not sure what I'd save their to begin with.

---

### Post by oldfred on 2013-03-05
I mis-read your 3GB /home. If it is that small it is better just to leave it inside / (root). So both can share the same unused space. 
I find the hidden user settings for /home take less than 500MB, but as soon as you start saving anything it can fill quickly.

I do not know multiple monitors but have seen several posts where users had issues. Depends on your video card and you may have to edit xorg. But some like to push the limits.

 12 monitors Natty Warhal
This is a success story for installing 3 ATI Firepro 2260's and 1 Radeon HD 5870 in the same computer. 
[http://ubuntuforums.org/showthread.php?t=1850517](http://ubuntuforums.org/showthread.php?t=1850517)

 ARandR Screen Layout Editor 0.1.4 - Dual screens
[http://christian.amsuess.com/tools/arandr/](http://christian.amsuess.com/tools/arandr/)

---

### Post by BlackTai on 2013-03-05
Thanks for all the help.  I'll retry in a day or to depending on my work load.

---

### Post by BlackTai on 2013-03-07
Okay, Round #2.  Well last time I installed ubuntu it worked(kinda), but those are all issues of separate categories that are not the pressing matter at the moment.  So when I did that, ubuntu was the only thing that would boot normally, causing me to manually select the the windows 7 partition from the boot menu in the uefi/bios menu if I wanted to boot into windows...  not ideal for how I'd like this computer to operate.

So, provided that I reinstall ubuntu in the same fashion(using 'something else' and manually partitioning drives), is there a way to manually make my computer to ask on startup which OS I want to boot from?

---

### Post by oldfred on 2013-03-07
If both Windows & Ubuntu are each installed in the same UEFI or BIOS mode, then the grub menu should let you select. And from grub you can select which system you want to boot as default. 

Otherwise you have to go into UEFI menu and select. And if not in same UEFI or BIOS mode, you have to turn that on or off in UEFI depending on which system you want to boot.

---

### Post by BlackTai on 2013-03-08
Okay well I'm not sure what to say then because it didn't.  From your earlier post you had said that I have windows installed in UEFI mode.  And I had run both a LiveUSB and a LiveCD in UEFI mode.  Both of them did not detect windows on my HDD.  I've attached some pictures of my system's boot menu in both EZ and advanced mode.  Something I see does raise a flag though.  In EZ mode I see that my system does not see my HDD in UEFI as it does with the Windows boot manager, ubuntu, and for my optical drive.  

Could that be an issue?  If it is, how then do I fix it?

---

### Post by oldfred on 2013-03-08
Most others that have posted UEFI screens have been similar to the old BIOS, yours is one of the first I have seen with all the graphics. That supposedly was one of the advantages of UEFI.

Is option ROM messages just messages or is force BIOS means it boots to BIOS mode not UEFI? 

I did not see secure boot settings for on/off on any of those screens or is it underneath something?

Does gparted from live installer show partition layout?

---

### Post by BlackTai on 2013-03-08
The description reads "Set display mode for Option ROM"
The User Manual reads:
 
[Force BIOS] The third-party ROM messages will be forced to display during the boot sequence.

[Keep Current] The third-party ROM messaged will be displayed only if the third-party manufacturer had set the add-on device to do so.

I also did not see any form of secure boot in any screen.  I somehow don't think my motherboard has that feature.

As for the gparted thing it appears to to be the same as the screenshot I posted earlier.  Or are you asking from different information?

---

### Post by oldfred on 2013-03-08
If it does not have Windows 8 pre-installed then it may not have secure boot. 

But all Window 8 pre-installed systems have to have secure boot and per Microsoft specifications to the vendors the user must be able to turn it off. Unless it is Windows RT which is not really Windows.

---

### Post by BlackTai on 2013-03-08
Yeah, It's a custom build, no Win8 of any kind...

---

### Post by oldfred on 2013-03-08
I do not know what else to suggest. UEFI should multi-boot without issue, if no secure boot. 

Someone posted this info on renaming a boot from his UEFI.
>  Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 
UEFI system only shows ubuntu. Delete ubuntu entry & reboot a couple of times & it resets to defaults including drives & USB ports.



---

