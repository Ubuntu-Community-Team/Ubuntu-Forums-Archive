---
title: "Problem with Dual Boot Win 8.1 &amp; Ubuntu 14.04"
date: 2014-05-14
forum: New to Ubuntu
---

### Post by joshua_gremo on 2014-05-14
Hello everyone, 

So this is my first time attempting to use Ubuntu and dual booting.  I have been following guides from official to unofficial ones. I get all the partitions ( / [root], /home, swap area, and bios_grub). It installs with no issues or so i think. Once it's done, i reboot the computer and it boots into windows ( apparently this is expected) I then reboot and boot from the livedvd and go to the "try ubuntu" and follow the directions to do the "boot-repair". If I do the recommended repair it goes good till it asks me to copy/paste 3 commands, which i do, they run fine, but the pop up from boot-repair stays and if i hit discard after it says it's cancelled.   Then I go the whole boot-repair thing and go to advance ( making sure the Grub location is "sda", purge before reinstalling, and unselecting repair windows boot files & check connection).

I do have the UEFI.   I'm not sure what to do anymore. I don't even want to really try again, spent all day trying to get this thing to work and right now it looks like its more trouble than it's worth. 

Sad to say I need to dummy's guide to installing Ubuntu 14.04 in a dual boot with  windows 8.1. I'm not sure if I'm missing anything so just let me know.

Thanks in advance!

---

### Post by oldfred on 2014-05-14
Post link to BootInfo report:
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If you installed 14.04, you should not even have to run Boot-Repair for many systems if you installed in UEFI boot mode. But if you installed in BIOS/CSM/Legacy boot mode then Boot-Repair makes it easy to convert to UEFI boot.

And some systems only let you boot Windows. Can you from UEFI menu or one time boot key, boot ubuntu entry?

---

### Post by joshua_gremo on 2014-05-14
Sorry I found my issue, but I encountered another which from what i've read is common with windows 8.1.

This is a portion of the full text I saved after finishing the boot-repair. 
Wrong GRUB version detected. Please report this message to [email]boot.repair@gmail.com[/email]

Reinstall the GRUB of sda8 into the MBR of sda
Installing for x86_64-efi platform.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

chroot /mnt/boot-sav/sda8 update-grub -y
Unrecognized option `-y'
Usage: grub-mkconfig [OPTION]
Generate a grub config file

-o, --output=FILE       output generated config to FILE [default=stdout]
-h, --help              print this message and exit
-v, --version           print the version information and exit

Report bugs to <bug-grub@gnu.org>.

chroot /mnt/boot-sav/sda8 update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
Unhide GRUB boot menu in sda8/boot/grub/grub.cfg

An error occurred during the repair.

You can now reboot your computer.

I sent it to the email provided. But is there any way for me to fix it myself without waiting for a reply?

"And some systems only let you boot Windows. Can you from UEFI menu or one time boot key, boot ubuntu entry?' 

I would have to look again, but from what i've read Toshiba laptops using the UEFI can do a dual boot. I just might have bad luck.

---

### Post by joshua_gremo on 2014-05-14
Done over 3 reinstalls, multiple boot repairs..looked at to many guides to list. Nothing works...either im still doing something wrong or my laptop isn't allowing dual boot.  thanks anyways.

---

### Post by oldfred on 2014-05-15
This says grub installed correctly as exit is 0
grub-install /dev/sda: exit code of grub-install /dev/sda:0

And it looks like Boot-Repair is adding a -y for yes perhaps in the wrong place. And then that causes an error on the sudo update-grub. (sudo not required if chrooted into your system).

With secure boot on or off?
What options does f12 or whatever your one time boot key show?
And in UEFI/BIOS can you set ubuntu as first boot option. 
Windows does like to reset it as first on any Windows update or maintenance.

---

