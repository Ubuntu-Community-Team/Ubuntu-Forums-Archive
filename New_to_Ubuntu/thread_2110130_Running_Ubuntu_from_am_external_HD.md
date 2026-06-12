---
title: "Running Ubuntu from am external HD"
date: 2013-01-29
forum: New to Ubuntu
---

### Post by viriatovigo on 2013-01-29
Good morning/afternoon/evening to every one.

I am new in this Forum and not too much knowledge of Linux, thought I used before -long time ago- Red Hat.

Last year I did install Ubuntu in an external HD and when starting Windows used to ask me if I wanted start on Windows or Linux.
But now I am using a Lenovo PC and goes straight away to Windows XP.

If I do press F12 I have the choice to start from the external HD but doesn't give the chance to go into the partition where is Ubuntu (or any other partition at all), so it says that can not start because there are not OS.

How can I resolve this issue, please?

With thanks in advance for your kindness,

viriatovigo
(Tino)

---

### Post by gordintoronto on 2013-01-29
It sounds like you are attempting to run Ubuntu from an external hard drive, where Ubuntu was installed using a different computer. It's possible that this will work, but more likely it will have a variety of problems, even if you can get it to boot.

The Lenovo might also have Secure Boot enabled. You need to turn it off.

---

### Post by Bashing-om on 2013-01-29
viriatovigo; Hi ! Welcome to the forum.

What apparently is not happening is a bootloader on the second drive, to boot up any operating system.
Here is one solution:
You will need a LiveCD/USB. Boot into the Live Environment and go to: ctl+alt+t ->Terminal;
```
sudo fdisk -l
``` to verify what/where is on the disks. The following is "assuming" the second disk is ubuntu AND seen as "sdb" with a series of numbers appended for the partition numbers.
Mount your OS partition:
```
sudo mount /dev/sdb1 /mnt
```Next, install GRUB2 (ubuntu's boot loader):
```
sudo grub-install --root-directory=/mnt /dev/sdb
```(Don't put a partition number in this command, just the HDD location a, b, etc.)
Now unmount:
```
sudo umount /mnt
```It is also possible may need to edit the file system table file to automount, will see.

Reboot.

It is your system, up to you how you want to boot. My suggestion for now:
Set in bios to boot the 2nd hard drive(ubuntu) as the first boot priority.
Boot ubuntu and log in;
ctl+alt+t -> terminal:
```
sudo update-grub
``` will rebuild the bootloader config files and pick up the windows system and chainload it --giving the option to boot up windows from ubuntu's grub menu.

We have not touched disk 1 (windows) and windows boot loader remains. If you need/want to only boot windows at some point/time, just reset the boot priority to the 1st hard drive in bios.[INDENT][INDENT][INDENT][INDENT]Make sense ?  
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by viriatovigo on 2013-02-13
Thank you both for y our advise.

In the end I've got enough and I did uninstall Ubuntu 11.10 from the external HD and install it again and end of the problem.

I have another problem now of different kind and I did a new post about it.

Once more, thank you very much.

All the best.

---

### Post by viriatovigo on 2013-02-24
Thank you to every one that did the best to help me.

The problem is resolved buy installing Ubuntu replacing Windows in the PC HD instead of installing it in the external HD.

It is working like a dream.

Once more, thank you to everyone.

All the best.

Tino

---

### Post by Bashing-om on 2013-02-24
viriatovigo;

You are quite welcome. Come back often.

[INDENT][INDENT]learning; an application of effort
[/INDENT][/INDENT]

---

