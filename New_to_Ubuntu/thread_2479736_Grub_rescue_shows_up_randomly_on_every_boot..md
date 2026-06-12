---
title: "Grub rescue shows up randomly on every boot."
date: 2022-10-05
forum: New to Ubuntu
---

### Post by adriantsai on 2022-10-05
Hello! I have a problem on my dell inspiron 15 5000 with a windows 11 and ubuntu dual boot on 2 separate drives, windows is on an nvme SSD and ubuntu is on a hard disk. The problem I have right now is that whenever I boot up Ubuntu, the "minimal bash like line editing is supported"  grub rescue screen shows up randomly(randomly as in perhaps it will show up in one instance of a boot but when I reboot the computer, the correct grub menu shows next time, only for the rescue screen to show the next time after that, etc.) I have run a boot repair which yielded this pastebin: [https://paste.ubuntu.com/p/DsbkZZCdnv/](https://paste.ubuntu.com/p/DsbkZZCdnv/). I am unsure of where the problem lies as the grub works sometimes, while it doesn't in others and I have followed tutorials on Youtube and forums for grub repair yet some of the commands I typed do not work. Here is the lsblk information:
 [IMG]https://i.imgur.com/Wkj9AQZ.png[/IMG]

[IMG]https://imgur.com/a/5QOci6V[/IMG]

---

### Post by tea for one on 2022-10-05
As you have two disks, it is ideal to separate both systems from each other and boot via the dedicated one time boot menu.

However, you have three EFI System partitions:-
nvme0n1p1	: is---ESP
sda5	: is---ESP
sda1	: is---ESP

Also, the disk sda (where Ubuntu resides) contains Windows boot files in sda1 but Windows is on the nvme disk?
The fact that Grub sometimes becomes confused, yet eventually boots is a testament to its strength.

Suggestion:-
Ensure that you have back ups of your personal files.
Re-install Ubuntu so that you only have one ESP per drive.
Disconnect, de-activate, isolate via UEFI settings or physically remove existing Windows OS nvmeon1 drive so that only the target drive is accessible
Boot Ubuntu live and check that you are in UEFI mode
Open a terminal and enter:-
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
```
Create GPT on your target disk using gparted
Open gparted > Device > Create Partition Table > Select gpt
Allow the installer to automatically create the necessary partitions (or your preferred configuration)

Double check that an EFI partition will be created
Boot each system independently via UEFI boot screen (ideal not cumbersome)
Boot priority can be controlled by UEFI
Each drive should have boot manager (Windows Boot Manager and Grub for Ubuntu)

De-activate, disconnect, isolate or physically remove one drive so that you can check if the other boots independently (and vice versa)

if you want to share files between each OS, then you can create a shared ntfs partition on the Ubuntu drive.

---

### Post by adriantsai on 2022-10-05
Thanks for the insight, I'll try it out!

---

