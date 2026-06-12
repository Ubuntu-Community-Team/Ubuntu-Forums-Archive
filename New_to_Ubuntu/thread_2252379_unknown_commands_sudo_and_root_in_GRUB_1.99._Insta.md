---
title: "unknown commands sudo and root in GRUB 1.99. Installing Ubuntu from USB."
date: 2014-11-11
forum: New to Ubuntu
---

### Post by Zachary123 on 2014-11-11
Hello,

As a favor to a friend I am installing the latest version of Ubuntu on his Sony Vaio VGN AR370. The laptop is in used condition and looks to already have GRUB 1.99 installed with a few OS's available. I've attached photos of the GRUB menu and the resulting output if I choose to boot any of the OS's.

All I would like to do is boot from a USB stick I have loaded with Ubuntu, however, I am having trouble. If I enter the command line from GRUB I can view the attached USB as hd1, but I cannot boot it. The commands sudo and root are not recognized, so I am having trouble finding resources for fixing this problem.

Is the problem that I have to reinstall GRUB?

Any input or direction is appreciated

Thanks,

Zack

---

### Post by deadflowr on 2014-11-11
You need to change the boot order of the machine, via the BIOS screen, or typically there might be an option to access the system boot options through a keyboard button, usually something like F2, or F10, or F12. Look for something mentioning boot when you first turn on the screen.(It''l most likely say something like Press F2 for Boot Menu, look in the corners as that is where it'll probably show up)

The machine itself controls which connected devices get read and in what order.
Typically devices include cdrom, network, floppy, and hard drive.(usb sticks can sometimes be considered under the hard drive, from what I remember)
The order the machine lists them is the order the machine will boot.
If a machine is set to boot from a hard drive, then it will not access/ look at a usb stick, but simply load the hard drive.
If it is set from a usb first, then it'll look at the usb first and boot, or if no usb stick or bootable media is found will skip to the next device in the order. Until a bootable media is found.
Hope that makes any sense...

---

### Post by Bashing-om on 2014-11-11
Ninja'd ! .. what deadflowr said.
[INDENT]boot up, take action
[/INDENT]

---

### Post by Zachary123 on 2014-11-11
Yes, that makes sense. Installing now. Thanks for quickly responding.

Aside: It looks like there are two hard drives and the previous owner had lots of partitions for each. What might have been the reason I couldn't boot into any of those listed OS's?

---

### Post by lisati on 2014-11-11
Sometimes a system will have partitions that can't be used directly for booting a computer. Windows, for example, often comes with extra partitions containing data useful for recovering your system should you want to restore it to an out of the box condition - these can be used by special software that let you prepare recovery disks. Some users also create partitions so they can keep their data and the OS separate.

---

### Post by deadflowr on 2014-11-11
> **Zachary123 said:**
> Yes, that makes sense. Installing now. Thanks for quickly responding.

Aside: It looks like there are two hard drives and the previous owner had lots of partitions for each. What might have been the reason I couldn't boot into any of those listed OS's?

It's possible that those entries might have been on a totally different disk, or on a disk where they where reomved/reformatted.
But grub will still list them until grub gets updated.

Case in point, I had a machine that dual-booted ubuntu and winXP, I removed the xp disk and until I updated grub, the grub menu listed the winXP install, though it never booted since it did not exist.

---

### Post by Zachary123 on 2014-11-11
Installed 11.04 on the 80GB drive /dev/sdb1, but I cannot boot it from GRUB. It immediately drops to BusyBox shell with initramfs. If I press ctrl-d, I get a kernel panic.

If I go back and try to boot from USB, I get the error /casper/initrd.1z: read error @ 20747779.

Does this all mean that there is an error in my init script?

---

### Post by Bashing-om on 2014-11-11
Zachary123; Hey;

The last linux installed becomes the primary booting system ( 11.04 is way way End-Of-Life !)
In bios have you set the 2nd hard drive ( sdb) to the higher boot priority ?

And yes, it is possible that a grub config file is corrupt, but If we are to trouble shoot this issue, delete 11.04 and install a current release ( 14.04 IF the hardware supports).

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by yancek on 2014-11-11
The image on the left in your initial post just shows an Ubuntu installation with a number of different kernel.  Nothing to indicate it had multiple operating systems.

---

### Post by deadflowr on 2014-11-11
> **yancek said:**
> The image on the left in your initial post just shows an Ubuntu installation with a number of different kernel.  Nothing to indicate it had multiple operating systems.

The entries below memtest are a different system.

To add, the way grub reads by default is to first look at the current system and it's kernel's installed, then adds memtest, then runs os-prober which finds any other existing systems and their kernels.
Even though the kernel versions are quite similar, you wouldn't load the current system's previous kernels after the memtest entries.
(Unless you've made a custom grub entry, which in this case seems unlikely)

---

### Post by cariboo on 2014-11-11
I'd suggest you chroot the install using the usb device you used to install Ubuntu, and then update grub. Once you have booted to the desktop, open a terminal (Ctrl-Alt-t) and run the following commands:

```
[list]
[*] sudo mount /dev/sda1 /mnt
[*] sudo mount -o bind /dev /mnt/dev
[*] sudo mount -o bind /sys /mnt/sys
[*] sudo mount -o bind /proc /mnt/proc
[*] sudo chroot /mnt
[/list]
```

You should now see a root prompt similar to this:

```
root@skynet:~#
```

Next you need to update grub, at the prompt type:

```
update-grub
```

the output of the command should look similar to this:

```
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.0-24-generic
Found initrd image: /boot/initrd.img-3.16.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.1 LTS (14.04) on /dev/sda2
Found Ubuntu Vivid Vervet (development branch) (15.04) on /dev/sda3
done
```

press Ctrl-d twice, then reboot.

---

### Post by Zachary123 on 2014-11-11
Hey folks,

It turns out the partition table on sdb was messed up. I installed 14.04 on sda and used Gparted to fix it.

Thanks again for all of the information.

Zack

I also updated grub.

---

