---
title: "Black screen with blinking cursor"
date: 2014-03-28
forum: New to Ubuntu
---

### Post by Tom_McClintock on 2014-03-28
Hello everyone,

This is my first day of trying anything Linux based, and decided to give Ubuntu a try. I figured I'd put my wife's 3 year old laptop to use, a samsung RF510. I've tried installing Ubuntu around 6 times now, and after every install on the first boot, I come to a black screen with a blinking cursor (_) I can't seem to get away from. I've been using a bootable flash drive with the ISO as my CD-ROM drive does not work. My last install I loaded the try Ubuntu without install option and deleted all partitions hoping that may fix something, but still no luck. I've been installing using the option that does not allow me to partition anything.

Would it it be normal that the try without install version would load but not the real install due to graphics issues? The system has an nvidia chipset. 

What other issues could it be? I've googled for hours but unfortunately can't seem to pinpoint what the issue is. Being completely Linux dumb doesn't help either!

Any suggestions would be appreciated.

Tom

---

### Post by bookrt on 2014-03-28
You most likely need to boot the USB stick in EFI mode. See if that option is available in BIOs. Alternatively, you may need to disable EFI in BIOS.
See here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If this doesn't work, it may be a graphics driver issue.

---

### Post by PondPuppy on 2014-03-28
Which version of Ubuntu -- 12.04, 13.10, or something else? I think the Samsung RF510 is a 64-bit machine, correct? In other words, it should run either 32- or 64-bit Ubuntu, so that shouldn't be an issue.

Could be a UEFI thing. I've had a similar thing happen with some distros (not Ubuntu, though) on a quirky little netbook I have. Unfortunately I'm not knowledgeable on that front. If you boot from the USB, find the GParted program. Run that and it will show partitions and flags. Post back the information -- partitions, filesystem types, flags. That may be a help in troubleshooting.

Edit -- bookrt posted while I was typing. Good suggestion from him. Get into the BIOS and look for options like "legacy boot" and/or "secure boot".

---

### Post by Navneet_Kumar on 2014-03-28
Just wait for 2-3 min then the ubuntu install screen will appear...if not then tey installing ubuntu with a bootable USB(made using unetbootin)..........this should solve the problem.........

---

### Post by Tom_McClintock on 2014-03-28
/dev/sda1. Fat32. Boot
/dev/sda2. Ext4. 
/dev/sda3. Linux-swap
Unallocated

ubuntu 13.10, and yes it's 64bit.

---

### Post by Tom_McClintock on 2014-03-28
Waiting does nothing. Will making a boot cd with another program really make a difference? Afterall , it is installing completely with no errors until after the reboot.

---

### Post by Tom_McClintock on 2014-03-28
The only option I see is legacy boot, which I should disable?

---

### Post by JKyleOKC on 2014-03-28
> **Tom_McClintock said:**
> This is my first day of trying anything Linux based, and decided to give Ubuntu a try. I figured I'd put my wife's 3 year old laptop to use, a samsung RF510. I've tried installing Ubuntu around 6 times now, and after every install on the first boot, I come to a black screen with a blinking cursor (_) I can't seem to get away from.
Since it's working properly when you do the install, and the problem doesn't show up until you reboot after the installation completes, it may well be a video driver problem. Try holding down one of the shift keys while you are booting (as soon as the first BIOS=generated screen finishes displaying). If this gets you a GRUB menu listing your boot choices, use function key F6 to get a menu of options, and select "nomodeset" from it. Then use the indicated keystroke (as I recall it, it's CTRL-X, but I'm not sure -- the menus should tell you though) to continue booting.

If this gets rid of the black screen problem, let us know and some of us can then tell you how to fix it permanently. If it doesn't, there are other things we can try.

Not all Nvidia video adapters are compatible with the most recent driver code published by Nvidia, unfortunately; I'm not familiar with the Samsung laptops so don't know if this is the problem. The "nomodeset" option disables an auto-configuration feature in the kernel itself that caused similar problems with many Intel chipsets, so it's worth trying in your case. If it does turn out to be an incompatibility, ways exist to let you roll back to a driver that's more compatible with your adapter.

Keep us posted!

---

### Post by Tom_McClintock on 2014-03-28
Jim,

since my last post, I tried installing 12.04 with the same issue. The first attempt gave me an error at the end that grub2 couldn't be installed and cancelled it all. I tried again making sure I was connected to the network and it installed but the same issue came back after reboot.The only way I can access any type of terminal is booting with the bootable USB drive. Once the options load to choose either to install or try, I can hit escape and what looks like a odd prompt loads with the command line "GRUB>".

can I do anything from here to try to resolve this? Function f6 did nothing from here.

---

### Post by PondPuppy on 2014-03-28
PS -- I think it's probably a good choice to leave the BIOS legacy boot enabled. IMHO the partitioning looks fine.

---

### Post by JKyleOKC on 2014-03-28
> **Tom_McClintock said:**
> Once the options load to choose either to install or try, I can hit escape and what looks like a odd prompt loads with the command line "GRUB>".

can I do anything from here to try to resolve this? Function f6 did nothing from here.That "GRUB>" prompt indicates that something is going wrong in the boot loader. Try choosing the "try" option, then when the desktop appears, press CTRL, ALT, and F3 all at the same time. This should give you a command-line login screen. The standard releases provide six "virtual terminals" and this will get you TTY3 (F1 would get TTY1 and so on; F7 will get you back to the GUI desktop). Once you have logged in (user name will be "ubuntu" and I think there's no password for it on the live CD -- if I'm wrong about that, try "ubuntu" for the password also) you will have a command line from which we can explore the installation on your hard disk. The first exploration would be to enter the command "mount" to get a report of all the things that have automatically mounted. That will give us leads for identifying the installation on your hard drive and exploring it.

And PondPuppy is absolutely correct. Leave the BIOS setting for "legacy" unchanged.

---

### Post by westie457 on 2014-03-28
With an ethernet cable connected boot using the USB stick into 'Try' Mode. Go to here. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) and follow the 2nd option.

When BootRepair is running click the 'Advanced' button, say no to any repairs and yes to generate a Boot Report.

Post the link here so we can have a look at what might be wrong.

Edit: Forget about the advanced options, just go for the 'Create Bootinfo Summary' button.

---

### Post by bookrt on 2014-03-28
Read the tutorial on EFI linked above closely. You can either boot in EFI mode, or disable EFI and boot in legacy. It sounds like Ubuntu installed in legacy mode but your chipset is set to EFI mode. You can also do a boot repair process to manually install an EFI partition.

---

### Post by squakie on 2014-03-28
Excuse me for putting in my 2-cents worth.  If you can actually install, then get the black screen with a blinking cursor when trying to actually boot the installation, then try the ctr/alt/F1 (or F2....F6) and see if a login request comes up.  If so, enter your username and your password (the password isn't echoed to the screen).  If  you can do that and get to a command line prompt (something like "$:", then Ubuntu is running and it's a video issue.  Personally, I would put the nomodeset option in the boot parameters and then reboot and see what happens.  A quick lspci | grep VGA should provide a small amount of output that would be useful for us as well, so if you can get this far, please post back the ouput.

If you do not get a prompt for a login, then Ubuntu hasn't booted completely and there is another problem.

Please post back those results.

---

### Post by Tom_McClintock on 2014-03-29
Is there a way to copy the text from within this terminal?

Also to note, I had some serious issues getting my computer to boot from my thumb drive, despite it being the first in priority and being recognized. I had to bring up the "Legacy" option in front of the flash drive, which was originally turned off for it to work. So the boot order goes 1. Legacy, 2. Flash Drive, 3. Hard Drive. I see nothing in the bios regarding EFI.. It's only a 3 year old computer, but the BIOS seems extremely plain. No fast boot option either.

I'll work on everyone else's responses this morning. Army is beating me up with work!

---

### Post by Tom_McClintock on 2014-03-29
> **squakie said:**
> Excuse me for putting in my 2-cents worth.  If you can actually install, then get the black screen with a blinking cursor when trying to actually boot the installation, then try the ctr/alt/F1 (or F2....F6) and see if a login request comes up.  If so, enter your username and your password (the password isn't echoed to the screen).  If  you can do that and get to a command line prompt (something like "$:", then Ubuntu is running and it's a video issue.  Personally, I would put the nomodeset option in the boot parameters and then reboot and see what happens.  A quick lspci | grep VGA should provide a small amount of output that would be useful for us as well, so if you can get this far, please post back the ouput.

If you do not get a prompt for a login, then Ubuntu hasn't booted completely and there is another problem.

Please post back those results.

Unfortunately, the screen does not allow me to do anything.

---

### Post by Tom_McClintock on 2014-03-29
So I just now noticed the EFI option in the bios. Legacy OS boot description says select disable to attempt EFI boot first, legacy OS boot second. It has been set to disabled.

---

### Post by bookrt on 2014-03-29
So has this fixed the problem?  Have you been able to redo the installation with legacy disabled?

---

### Post by Tom_McClintock on 2014-03-29
> **bookrt said:**
> So has this fixed the problem?  Have you been able to redo the installation with legacy disabled?

No, not fixed. The only way to boot is with the option in Bios: Legacy USB Support Enabled.

Here's how the BIOS options look that can boot with USB now:

Advanced Tab:
CPU Power Saving Mode: Enabled
Hyperthreading: Enabled
EDB (Executive Disable Bit): Enabled
Legacy USB Support: Enabled
Legacy OS Boot: Disabled
AHCI Mode Control: Manual
    Set AHCI Mode: Enabled
Fan Silent Mode: Auto
USB Charge In Sleep Mode: Enabled
......

Boot Priority ORder:
1. USB HDD: PNY USB 2.0 FD
2. AHCI HDD: Samsung HM500JI

Exclude from Boot Order:
AHCI CD
USB FDD
PCI SCSI
USB CD
USB Key
USB Zip
USB LS120
Legacy
.....

---

### Post by Tom_McClintock on 2014-03-29
> **JKyleOKC said:**
> That "GRUB>" The first exploration would be to enter the command "mount" to get a report of all the things that have automatically mounted. That will give us leads for identifying the installation on your hard drive and exploring it.


Below is what "mount" displayed.

/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

---

### Post by Tom_McClintock on 2014-03-29
> **westie457 said:**
> With an ethernet cable connected boot using the USB stick into 'Try' Mode. Go to here. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) and follow the 2nd option.

When BootRepair is running click the 'Advanced' button, say no to any repairs and yes to generate a Boot Report.

Post the link here so we can have a look at what might be wrong.

Edit: Forget about the advanced options, just go for the 'Create Bootinfo Summary' button.

Once boot repair opened, it said "EFI Detected. Please check options." Is that normal?

The link it provided me was [http://paste.ubuntu.com/7174244/](http://paste.ubuntu.com/7174244/)

---

### Post by JKyleOKC on 2014-03-29
Those results from "mount" seem to indicate that it's not even discovering your actual hard drive, which should show up as "/dev/sda1" in one of the entries, just as "/dev/sdb1" shows up on the 7th line of the listing. Apparently, your hard drive is partitioned with the "gpt" rather than the "legacy" method, and consequently the installation of Ubuntu didn't actually work.

I've managed to install on such a hard drive but it's been a while. I'll leave the details to squakie and bookrt since I don't remember exactly how I managed it and leaving a detail out could create even more confusion, but I do know that the Samsung implementation of EFI was/is a bit flaky and that in a dual-boot situation, both systems must boot in the same mode. If you can run the "Boot Repair" program as suggested, it will show a lot more detail -- but don't tell it to fix things until some of the experts here have looked it over, because it's possible it could make things worse.

---

### Post by Tom_McClintock on 2014-03-29
> **squakie said:**
>  A quick lspci | grep VGA should provide a small amount of output that would be useful for us as well, so if you can get this far, please post back the ouput.

Please post back those results.

From with the try mode, I opened Terminal and typed lspci | grep VGA and this is what came up:

02:00.0 VGA compatible controller: NVIDIA Corporation GT216M [GeForce GT 330M] (rev a2)

---

### Post by Tom_McClintock on 2014-03-29
> **JKyleOKC said:**
> Those results from "mount" seem to indicate that it's not even discovering your actual hard drive, which should show up as "/dev/sda1" in one of the entries, just as "/dev/sdb1" shows up on the 7th line of the listing. Apparently, your hard drive is partitioned with the "gpt" rather than the "legacy" method, and consequently the installation of Ubuntu didn't actually work.

I've managed to install on such a hard drive but it's been a while. I'll leave the details to squakie and bookrt since I don't remember exactly how I managed it and leaving a detail out could create even more confusion, but I do know that the Samsung implementation of EFI was/is a bit flaky and that in a dual-boot situation, both systems must boot in the same mode. If you can run the "Boot Repair" program as suggested, it will show a lot more detail -- but don't tell it to fix things until some of the experts here have looked it over, because it's possible it could make things worse.

Not sure why the windows partition is still showing. Windows has been removed from my understanding.

Sorry for my complete lack of ignorance in this matter.

---

### Post by JKyleOKC on 2014-03-29
Your Boot Repair report confirms the EFI-legacy conflict. I'll leave the "how to fix it" advice to others but will be keeping an eye on this thread in case I can help any more...

---

### Post by JKyleOKC on 2014-03-29
> **Tom_McClintock said:**
> Not sure why the windows partition is still showing. Windows has been removed from my understanding.That "windows" partition is, I believe, just the description for the CDROM partition it discovered, and means that it is "legacy" formatted. Only the partitions identified as "/dev/sda*" in the Boot Repair reports are on your actual hard drive, which is formatted entirely as "gpt" now.

No need to apologize for not yet being expert on a new-to-you system. I've been working with this stuff longer than most people here have been alive, and still haven't reached "expert" status on all of it!

---

### Post by Tom_McClintock on 2014-03-29
after running boot repair, it now seems to be working! 

Let me play around to make sure. While I wanted to run 13.10, I'm a little worried of trying if this works. Is there a big difference?

---

### Post by JKyleOKC on 2014-03-29
Since 14.04, which will be another Long Term Support version, is due out in just a couple of weeks, I'd not bother with 13.10. There's always fairly significant differences between one release and the next, but the basic feel won't change much...

---

### Post by bookrt on 2014-03-29
Glad this is finally working! I would say that you have worked this hard to get it running, now don't fix what ain't broke! I agree with JKyleOKC, wait until 14.04. You should be able to upgrade from within your current install (but back up your data before you do so).

---

