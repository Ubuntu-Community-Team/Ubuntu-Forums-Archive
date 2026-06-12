---
title: "Ubuntu on Lenovo s440"
date: 2013-11-22
forum: New to Ubuntu
---

### Post by manje2 on 2013-11-22
Hi all,

I am not necessarily an absolute beginner to Ubuntu, but I am to new hardware. I recently bought a new laptop, which is a Lenovo thinkpad edge s440.

It has a haswell processor, 8GB ram, in my case no touchscreen, and apart from 500GB HDD also a 16GB SSD. Now I am not sure what the SSD is used for, but I cannot access it as a separate drive. I think (and read something alike) that it is used by windows in some ways which makes it inaccessable, but please correct me if i am wrong.

I completely dislike windows 8, and was very pleased with Ubuntu on my previous laptop, so it would be nice if I could install it on my current laptop as well. I cannot, however, find any proper instructions to do so on this model as it is quite a new one.

Preferably, I create a dual boot with windows 8. It would also be nice if I could install Ubuntu on the 16GB SSD. Would you guys know perhaps, what would be the best way to go and if any of this is even possible?

Your input will be greatly appreciated.

Best wishes,
Manje

---

### Post by electrohandyman501 on 2013-11-22
I can't say much about W8 as I've not worked with one. If I was a betting individual I'd guess that the SSD is used as a swap file space. I've been reading hints in other posts about W8 and dual booting that W8 doesn't completely "shut down" it mearly "hibernates" and thus locks some areas of the HDD as being in-use and this appeard to cause issues with Linux.

---

### Post by DuckHook on 2013-11-22
The normal use for an SSD is either to house the OS itself, with /home, /swap, /var and /tmp on the HDD, or to use it as tertiary disk cache. The idea is that the OS will launch like lightning while heavily accessed partitions (cited above) are relegated to the HDD, thus extending the life of the SSD. I've dug up an old thread [here]("http://ubuntuforums.org/showthread.php?t=2112605&p=12494671#post12494671") in which I explained it fully.

---

### Post by oldfred on 2013-11-22
Is this an Ultrabook that also has dual video.
And you are booting with UEFI and secure boot.
I would at least to start plan on dual booting. Some system really need Windows to fix or update various things. 
Also with a new Haswell processor you need 13.10, but then next versions 12.04.4 in Jan and 14.04 have even more improvements.

The small SSD is used by Intel SRT as cache. And it uses RAID that can complicate install. It used to not install at all, but now grub just does not install correctly as it is not sure if it should install in RAID or standard efi mode.
  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

You have to turn off secure boot, fast boot,turn off SRT, remove RAID meta-data and decide if you want / in the SSD. If a Windows user you may want to turn SRT back on after installing Ubuntu only to hard drive. Some that are Ubuntu primarily install / (root) to SSD and have /home and other partitions on hard drive.

See more info in link in my signature.

From another similar SRT user.

 Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

      
 Intel Haswell - Linux support June 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU](http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU)

Even if a different brand computer, these Intel settings may apply to your Haswell system also.

 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

### Post by DuckHook on 2013-11-23
On these forums, always listen to *oldfred*. Good solid advice.

---

### Post by manje2 on 2013-11-23
Those are some very helpful answers. Thanks all.

---

### Post by matzipan on 2013-11-24
Hey,

Got an S440 a few months ago. Good choice, you're gonna love it. 

I did the same, left W8 on the HDD and installed Ubuntu on the SSD. To disable the SSD cache functionality in W8, you just need to go to Add/Remove programs and uninstall something like FastCache (can't remember exactly). 

Unfortunately, wasn't able to setup Switcheable Graphics, but on this laptop it's not such a loss, since the dedicated graphics is not that powerful. So in BIOS I just set it to "Always integrated".

I also needed to change a setting regarding UEFI legacy, can't remember exactly, but it's something along those lines...

You will also need to update to the latest kernel and manually install the binaries for the Wireless card , as Intel Wireless-N 7000s are extremely new (they were supposed to be launched in 2014), [http://askubuntu.com/questions/331667/no-wireless-for-intel-corporation-7260-version-63](http://askubuntu.com/questions/331667/no-wireless-for-intel-corporation-7260-version-63)

To enable two-finger scolling, you just need to go to the Settings panel in Ubuntu under mouse. 

HDMI works perfectly. Wifi crashes sometimes but turning it on and off from the keyboard button does the trick. I have the touchscreen version so I'm looking forward for Unity 8.

Everything else worked like a charm, I absolutely love this laptop. It is a shame I couldn't find it in a Windows-less version.

---

### Post by manje2 on 2013-11-26
Hi,

Thanks for the walk-through. Glad to hear you are so pleased with the laptop. I am a bit bummed about the difficulties with switchable grapics though. 

Have you looked at this? [URL="https://help.ubuntu.com/community/HybridGraphics"]
https://help.ubuntu.com/community/HybridGraphics[/URL]

If so, any idea why that did not work?

I do not really want to turn off my dedicated graphics card in the BIOS, because I might have to use it under windows.

---

### Post by fx182 on 2013-11-27
Hi Guys,

I'm also planing to buy this lenovo, thanks matzipan for the review :)

Manje, I don't know which version of Ubuntu you're trying to run but BTW I just found this: [http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work)

Keep us informed if you can have something working.

---

### Post by manje2 on 2013-11-28
Hi,

I have everything setup now with ubuntu 13.10. It does work with switchable graphics (with an upgrade to kernel 3.12), but not automatically and not without reboot. The good thing is, I won't have to change settings to integrated graphics in the bios. I will post the steps that I made for the current setup later. If I find the time, I will do this tonight. And again, everybody, thanks for the input.

Cheers,
Manje

---

### Post by fx182 on 2013-12-02
I also see the Lenovo S540, which seems to be the larger brother of S440. Does any of you heard if SSD can be used as separate drive like Matzipan did ? I think yes because S540 is the same family than S440 but not sure.

Cheers,

---

### Post by oldfred on 2013-12-02
In general we have seen many different brands & models of computers with the Intel SRT install Ubuntu. 

Some have used SSD only as root, some are more Windows users and turn SRT back on after Ubuntu install to hard drive only, and a few had larger 32GB SSD and the SRT only used a small part of SSD so they were able to install / (root) into part of the SSD and also have SRT on.

Some find one or two minor issues as showstoppers, others find Windows may have some issues also and prefer Linux.

As I understand it the newest Haswell or 4th gen Intel chips have video processors that are much improved and consume a lot less power. But because they are new, they are only in the higher end systems for now.

 Intel "Haswell" System 76 Iris Pro Linux Graphics Yield Some Wins Against Windows
[http://www.phoronix.com/scan.php?page=article&item=intel_irispro_linwin&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_irispro_linwin&num=1)

---

### Post by matzipan on 2013-12-18
@fx182: I just did not want to mess with X. I have had horrible experiences with it, and I'm a bit traumatised. I'm just gonna wait for weston/mir to mature untill I can try and use them.

---

### Post by manje2 on 2013-12-22
Hi, 

I just realized I forgot to post a guide - it's been busy. Here it is at last.Now Ubuntu 13.10 runs fairly stable, although I do get some errors sometimes and I cannot wake-up the laptop after closing the cover. Other than that, no problems.
Cheers,
Manje[B]

preparation[/B]

Create ubuntu 13.10 live USB (e.g. using Unetbootin).

**in windows**

Shrink windows partition for ubuntu.

turn off fast boot
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

specific to Lenovo: delete ExpressCache under windows (driver for SRT)
[http://forums.lenovo.com/t5/ThinkPad-Edge-S-series/S430-with-16GB-SSD-how-to-enable-caching-on-SSD/m-p/788463/highlight/true#M9092](http://forums.lenovo.com/t5/ThinkPad-Edge-S-series/S430-with-16GB-SSD-how-to-enable-caching-on-SSD/m-p/788463/highlight/true#M9092)

Before doing anything with Ubuntu, it might be wise to create a w8 recovery USB (to replace the w8 recovery partition).

**in the BIOS**

[I]Please note that these steps might not be necessary, but I followed them anyway. 
For more info check [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Turn off secure boot
    Set UEFI/Legacy Boot to [both]
    Set Boot priority to [UEFI First]
 
    Change boot priority to boot from USB[/I]

**boot USB**

Install root on ssd (format ssd) and the other partitions on the harddrive (the freed space)

[B]after installation
[/B]
First, to be able to boot you have to turn off switchable graphics in the BIOS.

Next, I upgraded to terminal 3.12. I read somewhere it should work better with switchable graphics. When I revert to 3.11, my discrete GPU does not work anymore.

To be able to use the the ATI videocard I installed proprietary drivers by typing in a terminal (I think having switchable graphics turned on is necessary):

sudo apt-get install fglrx fglrx-pxpress

After this I can switch between graphic cards and I don't have to turn  things on and off in the BIOS. You do however, have to reboot before the  other card will be used.

Edit:
I edited this post to leave out an upgrade to terminal 3.12 as it does not work anymore, when re-installing ubuntu. I was probably lucky that it ran in the first place. Also, I forgot to mention fglrx-pxpress, which without the ATI card doesnt work with switchable graphics turned on (so it wont work at all).

---

### Post by manje2 on 2013-12-22
double post

---

### Post by matzipan on 2014-02-13
> 
[COLOR=#000000]Before doing anything with Ubuntu, it might be wise to create a w8 recovery USB (to replace the w8 recovery partition).


I did not know that is possible, and I was afraid of installing linux on the HDD to not lose my windows recovery partition. Thanks!
[/COLOR]

---

### Post by Gordonbp531 on 2014-02-14
If you are going to dual-boot, then there's absolutely no need to turn off Secure Boot, or Intel rapid start or raid before installing Ubuntu >13.04.....but it must be the 64 bit version.
I have a Lenovo U410 Ultrabook, and 13.04 just installed without messing with any of that...

---

### Post by manje2 on 2014-02-24
I agree with you that secure boot might not be necessary at all. For the rapid start thingy however, I needed to turn that off (by uninstalling the driver in windows), so I could install ubuntu on the SSD (which was used by rapid start).

---

### Post by daniel145 on 2014-04-28
I did what you say here and ubuntu works fine, but windows disapeared.
I'm trying to reinstall it from the recovery copy I did but it seems to be corrupted.
Can some1 help me here? It is a new s440 and I don't want to lose warranty

---

### Post by matzipan on 2014-05-24
> **daniel145 said:**
> I did what you say here and ubuntu works fine, but windows disapeared.
I'm trying to reinstall it from the recovery copy I did but it seems to be corrupted.
Can some1 help me here? It is a new s440 and I don't want to lose warranty

Do you still have the problem? Make sure you unmount the NTFS partition from Ubuntu when you reinstall from recovery. Also, are you sure you disabled SSD caching?

2 months ago I installed 14.04. No more issues with wireless and the microphone and mute leds started working.

---

### Post by manje2 on 2014-07-11
> I did what you say here and ubuntu works fine, but windows disapeared.
I'm trying to reinstall it from the recovery copy I did but it seems to be corrupted.
Can some1 help me here? It is a new s440 and I don't want to lose warranty

A guess, but could it be that you put grub on your MBR (windows boot) partition and by doing so breaking windows' boot sector (I did that one time)?

If you haven't solved this yet and if you're able to get into windows recovery and from there the command line, there are ways to fix it. 

For example, see:
[http://www.techspot.com/guides/630-windows-8-boot-fix/](http://www.techspot.com/guides/630-windows-8-boot-fix/)

---

### Post by shalom3 on 2014-07-11
i just installed ubuntu onto my win 8.
make a partition in windows 8 for ubuntu (in disk management).

download ubuntu from internet. then save it in a USB or DVD. then boot it and install

---

### Post by oldfred on 2014-07-11
Never make partitions in Windows Disk management. It may convert to dynamic partitions and cannot make Linux partitions.
But do use Windows own Disk tools to shrink the Windows NTFS partition and reboot immediately so it can run chkdsk and make repairs. Leave as unallocated space for new Ubuntu install.

But only use Something Else if reinstalling. With Windows 8 the auto install options do not correctly see the Windows install and overwrite it. If you use Something Else you just have to choose the same ext4 partition as / (root) and reinstall to that.

---

