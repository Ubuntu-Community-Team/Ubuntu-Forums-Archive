---
title: "Installed ok, could not boot, boot-repair failed"
date: 2017-02-16
forum: New to Ubuntu
---

### Post by crazedhorsecat on 2017-02-16
Let me begin by saying I've never touched Linux before this week, so explanations of obvious things would be appreciated.  I've installed Ubunto Gnome from a usb. I tried to  boot the pc expecting some kind of os choice screen, instead I hit a dos  error saying 'no such device' and that grub was entering recovery mode.

  I dug around and found some suggestions that involved booting from a  live usb, which I assumed meant using the try Ubuntu option from the  installer. When I did this I got the desktop and everything there seems to be running ok.

Initially I tried a few things on the grub command line:

ls gives me:
  (hd0) (hd1) (hd1,gpt5) (hd1,gpt4) (hd1,gpt3) (hd1,gpt2) (hd1,gpt1) (hd2) (fd0)
  set gives me:
  cmdpath=(hd0)
  prefix=(hd0)/boot/grub
  root=hd0
  I have 2 non ssd hdd disks, one is Windows, the other is media files  and Linux. I have no idea how this relates to what I'm seeing.

  Then I attempt to follow this guide: [http://askubuntu.com/questions/373385/how-do-i-fix-grub-rescue-uninstallation](http://askubuntu.com/questions/373385/how-do-i-fix-grub-rescue-uninstallation)

  At the step asking to step through all the volumes, every single  volume returns error: unknown filesystem, except for (fd0) which returns  error: failure reading sector 0x2 from 'fd0'.

Then following someones advice I tried:

Running gparted, I got a warning saying the driver descriptor says  the physical block size is a different size to what Linux reports it as.  I continued and located the three windows, linux and swap partitions.

I've run boot repair, which seemed to running fine until the end of  the process when it said an error had occured  (with no details), but  also said the process was complete and I should restart.
  I did and still cannot boot to anything other than the grub recovery command line. Here is a link to the boot repair output: [http://paste2.org/vnXV46p9p]("http://paste2.org/vnXV46p9")

I've seen various suggestions for switching bios features on and off, but none of them seem to exist on the menu I see when I go to the settings.
My Googlefu is failing me at this point and I don't really know where to go from here.

Edit: 
I just discovered I have no sound when running from the USB stick :(

---

### Post by oldfred on 2017-02-16
May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Best not to run the auto fix, until someone has reviewed the report.
auto fix often works, but many times other fixes that Boot-Repair cannot do,  or use of advanced mode is required.

---

### Post by crazedhorsecat on 2017-02-16
Hey oldfred

As requested, the output of boot-info: [http://paste2.org/e4EOKM0a](http://paste2.org/e4EOKM0a)

Thanks!

---

### Post by oldfred on 2017-02-16
Most of the errors I see you can ignore.
Both Windows system reserved & bios_grub have to be unformatted. But since unformatted, Boot-Repair tries to mount as Windows NTFS and cannot, so gives errors.
Some of the other errors are related to flash drive. And those can be ignored. The one time recently where I used a flash drive I got the 2048 sector warning.

And it looks like grub is correctly installed to sdb. If from BIOS you directly boot that does system now boot?
And best to install a Windows boot loader to sda.

Boot-Repair's auto fix always installs grub to the MBR of every drive. Better to have Windows boot loader on Windows drive and grub2's boot loader on Ubuntu drive.
You may be able to use Boot-Repair to install a Windows like, boot loader to sda using advanced options, choose Windows and choose sda. Or use your Windows repair/install disk and its repair console to run fixMBR.

You also installed grub to sdb4's partition boot sector. That is almost never correct as there is no way to use it. The partition boot sector is not normally used, so not an issue.

You show no boot flag on sdb. Grub does not use boot flag, so not really required for Ubuntu/grub. And with gpt the boot flag is supposed to only be on an ESP - efi system partition.
But a few BIOS will not let you boot unless you have a boot flag (assumes Windows which must have boot flag?). 
If not ever installing Windows to sdb, convert the sdb1 - Microsoft reserved partition to FAT32 and add boot flag. That will then be an ESP, but only then used for UEFI boot which you are not using.
Microsoft just wants a reserved partition before any NTFS partitions used to boot from, before the install, so it often adds it first.

---

