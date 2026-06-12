---
title: "Flash drive unmounting"
date: 2024-11-04
forum: New to Ubuntu
---

### Post by planemad on 2024-11-04
Hi. I can't get through installation. I've tried on 2 reasonable laptops.
Straight into usb3 port (XPS) or powered USB 3 hub(surface pro)I just tried another distro, more lightweight. The 128gb Kingston, or other USB drive, both new, seem to become unmounted during installation every time. I'm totally new to Linux. I'm seeing a pattern. 2 reasonable laptops. Same or similar problem on both on 2 distros.
I think the problem may be lack of power to the USB hubs.
If any ideas?
Thanks

---

### Post by yancek on 2024-11-04
>  I've tried on 2 reasonable laptops.

Could you define the above term.  Age of the computers, RAM, CPU, etc.
Do you get any messages on screen?  Does it or do they all fail at the same point in your installation attempts and if so, what is it?

---

### Post by planemad on 2024-11-04
Surface pro 5 8gb, i7
XPS 9530(2013)16gb.i7.
Both fail at this command, with either flashdrive, with persistence on 1, or install to 2 USB drive. Always at this command. 
[ extracting image from... tmp/mount. ]
With AV Linux,Both laptop fail at 11% installation , and flash drive unmounts, with a popup message.. Unmounted, exceed time limit or something..? 
Cheers.
Otherwise, they are good laptops No issues

---

### Post by yancek on 2024-11-04
I've never used a Surface Pro but people appear to have more problems with them than other computers. So did you download the Ubuntu iso from the official Ubuntu site?  After downloading the iso, did you do an md5checksum to verify the iso was not corrupted during the download process (explained at the Ubuntu download site)?  How did you write the iso to the usb you are booting from, what method or software did you use?  How does persistence fit in?  Did you use some software to create a bootable usb with persistence to use as an installer?  Are you trying to install from one usb to another usb or are you trying to install to an internal hard drive?  Or, are you trying to install to the same usb you are booting from with the toram option?  If the latter, did you create free space on the drive on which to install Ubuntu? 

>  [ extracting image from... tmp/mount. ]

I don't recall ever seeing that error before.

---

### Post by planemad on 2024-11-04
Yes. I heard that. Tho I'm getting identical problem on both laptop. Yes I got the official download and did the checksum check. I'm using Rufus. I've tried every combination. The manual partitioning does a boot position for the kernel, persistence /efi, and ext4 , or a second usb. Setting persistence in Rufus, most of the flash drive

---

### Post by yancek on 2024-11-05
How does persistence fit in here?  If you are booting from a usb and trying to install to a hard drive there is no need for persistence.  That is usually just used on a 'live' usb so some data can be saved.

Do you have a windows OS installed on either or both machines?  If so, did you shrink the windows partition to create free space on which to install Linux?  If you have windows, is it an EFI install?  If it is, you won't need to create another EFI partition as Ubuntu will create a separate directory on that EFI partition for its boot files.  Again, if you have windows installed, do you have a separate physical drive on which you are installing your Linux?  If that is the case, you can create a separate EFI partition on that drive but it is not necessary.  Also, you don't need a separate boot partition unless you are using the LVM/Encryption method.

If you can boot the install media and open a terminal, try running the command below and posting the output so we have more details.  It won't change anything.

```
sudo parted -l
```

---

### Post by planemad on 2024-11-05
Windows 10 is on both laptops. I want to run Linux from just USB. So I can plug it into either laptop or other computers and just carry on with program/files etc. I type the command you give me. Yes it shows the USB drive. The problem is it gets unmounted during installation.

---

### Post by yancek on 2024-11-05
What instructions are you using?  You are using rufus on windows to try to create a persistent usb, correct?  That is not the same as installing Ubuntu to a hard drive or a usb drive.  A persistent usb will not be able to do everything you can do with an installed system.  The link below explains how to use windows with rufust to create a persistent usb so read through that and compare it to what you have done.  In your post above you refer to the manual partitioning method but if you are creating a live usb, rufus should handle that.  I haven't used windows in years and have never used rufus as I have never seen the need even when creating a persistent usb.  Your responses are a bit cryptic and you don't answer many questions.  If you don't know how to do something just say so.  I really don't know what would be going on while you are using rufus that would unmount the usb partition but as I said, I've not used rufus.  Maybe the link below will help.

 [https://itsfoss.com/ubuntu-persistent-live-usb/](https://itsfoss.com/ubuntu-persistent-live-usb/)

---

### Post by planemad on 2024-11-05
Thanks for the reply and the link. I've tried that 100 times. The same as those instructions. Flash the iso on with Rufus, with or without partition. Boot into it. installation starts fine, then stalls at same place on both laptop, both distros.it's something else.  manual partitioning is only option I have in Ubuntu studio, I don't want to delete windows. Avlinux same result. With or without partition

---

### Post by TheFu on 2024-11-05
> **planemad said:**
> Windows 10 is on both laptops. I want to run Linux from just USB. So I can plug it into either laptop or other computers and just carry on with program/files etc. I type the command you give me. Yes it shows the USB drive. The problem is it gets unmounted during installation.

Typically, you need 2 different drives.  1 with the ISO file on it and the other to receive the installation.  Could this be the issue?

Rufus has been giving people issues for a few years.  Maybe try a different ISO copy method?  mkusb or cp are how I do it.  Of course, if you setup Ventoy, you can have lots of ISOs and boot from any of them and have some persistent storage, but getting persistence storage to work on a bootable flash drive is non-trivial.  Best to use an internal HDD.

I wouldn't expect any MS-Surface to run Linux.  I didn't look, however.  Aren't they basically locked MS-Windows-S platforms?

I've never had issues installing Ubuntu onto any Dell laptop.  They sorta "just work", provided the BIOS settings are correct for Linux.  There are some that conflict with MS-Windows, however, so it is best to make the BIOS changes BEFORE allowing MS-Windows to finalize that install.

The flash drive that get the ISO on it, doesn't need anything pre-setup. It just needs to work.

Also, don't use any "USB hub" for these storage devices.  External USB hubs are known to interfere with lots of different hardware, causing problems.  Directly plug in the flash drive with the ISO into a USB port ON THE COMPUTER.  Same for the USB drive you are attempting to install onto.

If your computers have nvidia GPUs, you may need to look up specific grub boot commands.  For intel and amd iGPUs, I've never had this issue.

---

### Post by planemad on 2024-11-05
That's some great info. Ye, the surface might be one issue.. anyways, some things to look into, . Yes I think the hub may be an issue. The surface only has one port unfortunately. maybe the USB 3 ports on the Dell aren't up to to the task either..
I've tried partitioning 1 drive or using 2 external drives. 
It's the consistent same results I get, on 2 distros,2 laptops,every time, no matter what I do... hub, no hub, partition, no partition etc etc that gets me thinking..?? Scratching my head
 Cheers!

---

### Post by TheFu on 2024-11-05
Not all flash drives are compatible with all USB ports and not all are able to support booting.  This is less an issue on recent laptops (from about 2017), but prior to then, it wasn't uncommon to find that some flash drives couldn't be used for installations.  I had luck with cheap and expensive "brand name" flash drives.  Also had some bad luck with some cheap and expensive name brand flash drives, so there's no way to know, except to try them out.

Also, be certain that the BIOS in the computer is up to date AND that any Intel RAID options in the BIOS are disabled.  You want AHCI for all storage.

---

### Post by yancek on 2024-11-06
> The surface only has one port unfortunately 

How would you use rufus to create a bootable usb, then try to boot that usb and install your chosen Linux to another usb if you have only one usb port??  Best give up on that and stick with the other machine.   Using a hub to connect the second usb is just going to complicate things.  You could boot the usb and use the toram option on booting the usb if you have enough RAM (unknown to us) and the usb is large enough  but that is a little too convoluted for this case so best to stick with the Dell.


> I've tried partitioning 1 drive or using 2 external drives. 

What does that mean?  Some of your posts seem to indicate you have successfully written the Linux iso to a usb and have booted it and are having problems installing it.  What does partitioning drives have to do with the situation.  Are you trying to install from a usb you created with rufus to another usb or from a usb you created with rufus to to an external hard drive? 

How about booting the usb on which you have Ubuntu or whichever Linux you are now using, the one created with rufus and opening a terminal and running the command I suggested earlier to show drive/partition information.  Both usb drives attached when you run it. 

[QUOTEI don't want to delete windows] [/QUOTE]

How would you delete windows if you are installing from one usb to another usb?  Are you familiar with naming conventions in Linux so you can identify different hard drives or usb drives.

---

### Post by TheFu on 2024-11-06
With all this trouble, why not just skip using dual boot and go for a virtual machine install instead?  Then you can practice doing as many installations and seeing them work a few times before going back to your desired "carry-with-me" Linux solution.  I've been running my main Linux desktop inside a virtual machine since around 2008.  It is very portable and has been through base hardware and OS changes multiple times.  Using VMs skips all the local hardware issues.

---

