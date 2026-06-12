---
title: "Installing windows AFTER Ubuntu"
date: 2014-02-17
forum: New to Ubuntu
---

### Post by zaanta2 on 2014-02-17
Hi everyone......I need some advice please!
And in really, really simple words - I have no technical knowledge at all!

OK - I have a Dell Inspiron Laptop 64 bit - less than a year old. It came with W8.
I took it off........completely. I was so sure I would never need W again. Big mistake!
I know I should have dual booted leaving w8 on but I didn't. So....
I've hunted around here for possible solutions & - correct me please if I'm wrong - it seems to me that it's not possible to
install Windows as a dual boot situation when I have my OS 100% Ubuntu? (I have Ubuntu 13.10) Is this really true?
If it IS possible, could someone please explain to me - simply! - how to do it.
The reason I need this is that, for my work, there are some software programs that I must have which are just not compatible with
Ubuntu and will also not run on Wine.

Any advice/information would be greatly appreciated.

Cheers,
david

---

### Post by 3rdalbum on 2014-02-17
There are two ways of doing it:

1. Install Windows in a virtual machine; that way it runs on top of Ubuntu, inside a window. Pros: Don't need to reboot to get to Windows, don't need to repartition to install Windows. Cons: A performance penalty, you can't use 3D acceleration (so no games on Windows).

Go to Virtualbox.org and download Virtualbox for Ubuntu. Run through the wizard to set up a new virtual machine, and set the boot device to the Windows CD (or an ISO image of it). Run the Windows CD through the virtual machine; it will only be able to see the virtual disk image, so let it take up the whole disk. Easy!

2. Install Windows as a dual-boot with your existing Ubuntu. Pros: Full performance, you can game on Windows. Cons: Need to reboot to get into Windows. Need to partition.

Back up all your data. Boot the Ubuntu CD. Run Gparted. Resize your Ubuntu partition down to allow free space for Windows (for instance, leave 80 gigs free space on the hard disk if you want Windows to have 80 gigs of space).

Reboot and run the Windows installer. It will not be able to detect the Ubuntu partition, but it will see that there is free space. Use the Windows installer to create a new partition in that free space, and install Windows there.

After Windows is installed, it'll wipe out the GRUB bootloader, so you just need to reinstall it. The easiest way to do that is to run the Ubuntu live CD, install [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair"), and run it on "Recommended" settings.

Both methods work, it just depends what you prefer to do.

---

### Post by oldfred on 2014-02-17
Did you make a full backup image of your install? That can be restored.
Otherwise you have to purchase a full new copy of Windows as your product key in the UEFI is only for the UEFi OEM vendor version. Some vendors may send you for a nominal charge a new image, others will not.

 Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)

Did you install Ubuntu in BIOS or UEFI mode. And if in BIOS mode is drive partitioned with gpt or MBR?
Windows only installs to gpt partitioned drives with UEFI, where Ubuntu can boot with either BIOS or UEFI.
Both Ubuntu & Windows only boot from MBR partitioned drives with BIOS, and you have the 4 primary partition limit where Windows has to boot from a primary partition.

---

### Post by zaanta2 on 2014-02-19
Thank you both for your help/advice
The suggestion from 3rdalbum re using virtualbox sounds like the easiest (for me!) solution.
As I'm not a gamer, performance sufferage is not a problem.........I don't need use windows THAT often anyway.
Again, many thanks for your help,
david

---

### Post by johncallicrate on 2014-04-10
3rdalbum, have you tried other vm, like QEMU?
I have been on virtualbox for about 2 years,
and wondered about trying something else.

---

