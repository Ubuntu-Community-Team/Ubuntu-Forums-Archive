---
title: "Can't Install Ubuntu 12.10 with AMD Llano A8 3870 / EFI problem?"
date: 2013-04-03
forum: New to Ubuntu
---

### Post by RichardBruce on 2013-04-03
Ok, so I know what your thinking, "why cant people just google and find out about nomodeset?", right?

Well I did find out about nomodeset, but I'm not sure I'm using it correctly. 

I'm trying to install ubuntu from a USB drive created with LiLi (Linux Live USB Creator), but when I boot from my USB drive I get a black and white screen which say "GNU GRUB version 2.0-7ubuntu11" at the top and has some options (Install Ubuntu Server, Install in expert mode, OEM install) underneath. I select "Install Ubuntu Server" and press 'e' (I also pressed f6 for good measure). This gives me another black and white screen with the same title and the following text

setparams 'Install Ubuntu Server'
set gfxpayload=keep
linux /install/vmlinuz file=/cdrom/preseed/ubuntu-server.seed quiet --
initrd /install/initrd.gz

I change this to 
setparams 'Install Ubuntu Server'
set gfxpayload=keep
linux /install/vmlinuz file=/cdrom/preseed/ubuntu-server.seed quiet nomodeset --
initrd /install/initrd.gz

and hit f10 to boot. The the screen goes black, the monitor doesnt go to power save, but nothing else happens.

I was wonder about the "/cdrom/" given that I'm installing from a USB stick, so tried ...file=/preseed/..., but no luck

Ideas anyone?

---

### Post by RichardBruce on 2013-04-03
One thing to add.

 I do have a UEFI system that seems to have caused trouble in the past, but Lili looks to have create a UEFI device for me (UEFI appears before my USB drive when I choose to boot from it)

---

### Post by RichardBruce on 2013-04-07
So after some trial and error I've worked out that this is EFI related. I can start installing from a DVD in BIOS mode (even without nomodeset et. al.), but not EFI mode. The problem is now that I have 4 hard disks and only 4 SATA connections, therefore I must install from USB. If someone could answer one of these two questions I would be happy:
1. How to make EFI booting work, see below?
2. How to force my USB drive to boot in BIOS mode?

I would prefer option 1. So some more details. I have tried multiple Ubuntu versions now (11.10.12.04, 12.10, 13.04 beta) one version of Kubuntu (12.10 I think) and Fedora 18. All the (K)Ubuntu versions left me with a black screen as described above. Fedora, after following similar step as above, left me with a screen that said "Secure boot not enabled". I have hunted through my motherboard (ASUS f1 A55-M LK R2.0) manual and BIOS pages and cant find anything that looks like it's related to secure boot. Kind of stuck some more :(

EDIT:
One thing that might be relavent. My PC has never had any Windows version installed on it.

---

### Post by oldfred on 2013-04-07
Only systems with Windows 8 pre-installed have secure boot (so far). I would expect newer motherboard may have the secure boot setting.

But the newest versions of Ubuntu have UEFI secure boot capability, but I would still suggest those as they also have to newest UEFI fixes. Some of the older UEFI versions required major effort to get working, and with secure boot and the variety of UEFI implementations even new systems require a lot of effort.

Are you installing Desktop or Server?

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

What video you do have. nomodeset is most common with nVidia but may work with some others. I have nViia and have to use nomodeset on every boot of a live installer and first boot after install or until I get nVidia driver working.

With UEFI the install boot is with grub and adding nomodeset or other boot options is more like a first boot, in that you use e on grub menu and edit linux line.
      
 Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If you do not have Windows you can install in CSM or BIOS boot mode. Ubuntu will boot from gpt partitioned drives in either UEFI or BIOS mode. If you install with MBR(msdos) partitioning you will only be able to boot in BIOS mode. Even if reverting to BIOS mode I would use gpt and leave room or have an efi partition at beginning of drive so later you could convert to UEFI install. Boot-Repair will convert a BIOS install to UEFI if gpt partitioning and you have the efi partition. It basically uninstalls grub-pc(BIOS) and installs grub-efi(UEFI).

---

### Post by RichardBruce on 2013-04-08
Thanks for the reply. 

To answer some of your questions I am trying to install 64-bit server builds of Ubuntu 12.10 and 13.04 beta. I have ATI graphic, the Llano comes with an ATI graphics chip built in. My boot media is UEFI enabled because I can see UEFI: before the drive name when I choose which device to boot from. I am not trying to do a dual boot, I want ubuntu and only ubuntu on my machine.

I dont think the problem is graphics related because I can boot from a CD in BIOS mode. I did try nomodeset in EFI mode, but I got the same blank screen after the Grub menu. I will follow the advice in one of your links and add "nosplash --verbose text" to the boot command line, hopefully I can get some useful output.

---

### Post by RichardBruce on 2013-04-08
So, with Ubuntu 12.10 64-bit sever, I tried adding a whole bunch of options on the "linux        /install/vmlinuz...." command (nosplash, --verbose text, resume...), but none of them produced any output.

Then I tried pressing 'c' at the grub menu to get the grub> command line interface. From here I run the commands:
grub>set gfxpayload=keep
grub>      linux        /install/vmlinuz file=/cdrom/preseed/ubuntu-server.seed nosplash nomodeset --
grub>      initrd       /install/initrd.gz

All of these command completed quickly, but still Unbuntu wasnt installing. Its almost like I'm missing some command lines so i tried:
grub>boot

This is still running.

I must be missing something big and obvious here......

---

### Post by oldfred on 2013-04-08
I have nVidia and nomodeset works for me.

I believe the gfxmode setting is grub trying to use the system's video not some lower level driver.
 You can try this or whatever you monitor uses.
gfxmode=640x480

I think some just use generic setting to get something working also:
Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

[LIST]
[*]Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1 
[*]nVidia: nomodeset 
[*]Generic: xforcevesa or nouveau.modeset=0 
[*]Radeon: radeon.modeset=0 
[/LIST]

---

### Post by RichardBruce on 2013-04-08
I tried some of these options (radeon.modeset=0 and set gfxmode=xxx), but afraid all i have to report are some black screens.

In the command below <here> is the correct place to be putting these arguements (except gfxmode on the line above) isnt it?
set gfxmode=xxx
linux /install/vmlinuz file=/cdrom/preseed/ubuntu-server.seed quiet <here> --

I just found `set gfxmode=${GRUB_GFXMODE}` to try later

Some "good" news though it that from the grub command line "testvideo" worked for me. I got a black background with some coloured squares and "the quick brown fox jumps over the lazy dog" written on the largest square. So something is working.

---

### Post by oldfred on 2013-04-09
Are you not getting this line. If not do you have UEFI booting on?
I do not have UEFI but this is from my 12.10 ISO:

    linux    /casper/vmlinuz.efi.signed  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --

And yes replace quiet splash with nomodeset or whatever boot option(s) may be required. Sometimes one for Video and others for other issues.
Some have reported these, but every system is different and I do not know if Intel or AMD.
 Some systems need these boot parameters
ACPI=Off nomodeset 
pci=nomsi noapic
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w

      
 [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll

---

### Post by RichardBruce on 2013-04-09
> **oldfred said:**
> Are you not getting this line. If not do you have UEFI booting on?
I do not have UEFI but this is from my 12.10 ISO:

linux /casper/vmlinuz.efi.signed file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --


Thats interesting. From the grub menu I press 'e' on "Install Ubuntu Server" and all I see is
[QUOTE=RichardBruce]
setparams 'Install Ubuntu Server'
set gfxpayload=keep
linux /install/vmlinuz file=/cdrom/preseed/ubuntu-server.seed quiet --
initrd /install/initrd.gz
[/QUOTE]

My USB drive is appearing with "UEFI:" before the drive name when I select the boot device. I tried to create the USB drive with LinuxLive USB creator and UNetBootin, both gave me the same commands. I will have a look around the drive to see if i can find the files your ISO contains.

EDIT:
Mystery solved, you're looking at a desktop build and I'm looking at a server build. Thats why the commands are different, but I guess I should try the desktop build.

---

### Post by oldfred on 2013-04-09
They posted that the server has secure boot also. But I think the kernel is the same either way or secure boot kernel boots standard systems also, so maybe just the name is different? 
 As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI.

---

### Post by RichardBruce on 2013-04-11
Could this be something other than graphics related?

I have tried all the graphics related option we can find in GRUB, I even tried plugging into my HD tv, but still just black screens.

---

### Post by oldfred on 2013-04-11
Some have needed both graphic card entry and other boot parameters like I mentioned in post #9. Unless you can find a poster with exactly your system you just have to try alternatives, and even then users rarely come back and tell us exactly what they did, they just say it worked.

---

### Post by mywindow on 2013-04-12
I had a similer problem with my setup too. It ended up being because I had mild overclock settings enabled. Try resetting your bios and then configure with optimal settings and try from there.

My Setup:
AMD A-8 3850 FM1 with intergrated ATI BeaverCreek [Radeon HD 6550D]
Biostar TA75M+ Motherboard

---

### Post by RichardBruce on 2013-04-13
For now I'm working around the problem. I borrowed a cd drive and installed in bios mode from the cd (cant work out how to do this from USB), but it worked first time (no need for nomodeset, acpi=off, nothing)! I'm not sure if this counts as solved?, but thanks for all the help.

Now I'm just left with the unenvious task of changing the CD drive back to a hard disk and configuring software raid post install. I found a couple of articles on these forums on how to do this, so will hopefully be ok.

---

### Post by gordintoronto on 2013-04-14
Hi Richard, is there some reason you really need Ubuntu Server? You can do everything in Ubuntu Desktop that you can do in Ubuntu Server, and it has a lot less hassle. It looks like you have a pretty high-powered computer, so the slight extra overhead probably would not affect anything.

BTW, one of the facts you might have mentioned in your thread is what motherboard the computer has. Not relevant if the issue is solved.

Most people setting up a server want something they can leave alone for years. 12.04 might be a better choice than 12.10 or 13.04.

For making USB sticks, I use Unetbootin from Linux, or pendrivelinux from Windows. For me, both have provided better results than the program you used.

---

### Post by RichardBruce on 2013-04-21
I'm going to mark this as solved because I basically have what I want now.

For reference, my mother board is an ASUS F1 A55-M LK1 R2.0. I was unable to install in EFI mode or create a USB stick that booted in BIOS mode. I tried several (K|U|X)buntu version and serveral ways of building the USB drive (LiLi, Unetbootin and pendrivelinux). I tried several boot options (nomodeset, acpi=off... see thread for details). Nothing worked. My solution was to borrow a DVD drive and install Ubuntu 13.04 desktop in BIOS mode from DVD.

Thanks everyone for their help. Hope this save someone some time.


EDIT:
Sorry, how do I mark a thread as solved?

---

### Post by oldfred on 2013-04-21
Glad you eventually found a solution. Did you use gpt partitioning with UEFI, so you may be able to easily experiment with UEFI or is drive MBR(msdso).

See my signature for the workaround with the new forum until an add-in is installed.

---

### Post by RichardBruce on 2013-04-22
I didnt ask to not have gpt partitioning, I just handed everything over to Logical Volumne Manager :). I would assume I have gpt partitioning, but will have to check when I'm at the machine.

---

