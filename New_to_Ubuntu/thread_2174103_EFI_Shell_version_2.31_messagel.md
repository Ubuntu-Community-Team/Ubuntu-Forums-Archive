---
title: "EFI Shell version 2.31 message:l"
date: 2013-09-12
forum: New to Ubuntu
---

### Post by ryan29 on 2013-09-12
I was in the process of partitioning my hard drive and was chageing boot settings in my BIOS menu and at some point when I restarted the black page with EFI Shell version 2.31, popped up and now to even boot into ubuntu i have to type exit, then enter, and it takes a sec then boots me, how can I get around having to do this every time? Thank you!

---

### Post by Jonathan Precise on 2013-09-12
Run boot-repair found in "[linux secure remix]("http://sourceforge.net/p/linux-secure/wiki/Home/")" and post the link given and any error messages.

---

### Post by ryan29 on 2013-09-12
[http://paste.ubuntu.com/6099365/](http://paste.ubuntu.com/6099365/)
this is the url I get from boot repair.

---

### Post by Jonathan Precise on 2013-09-12
> The boot files of [The OS now in use - Ubuntu 12.04.3 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

Please use the windows partitioning tool to move the windows partition 1GB. Then use GParted to make an ext4 partition (1GB) labeled ubuntu-boot. Make sure it is at the beginning of the drive. Note the partition name. Example: /dev/sda1

Then run boot-repair with advanced options. In grub location, check "Separate /boot partition". In the combo box, choose the partition name you got in GParted.

Apply. Note the address. If it works, mark this as solved. If not, give us the new link.

---

### Post by ryan29 on 2013-09-12
Okay I have an unallocated amount of space at the beggining that is 266mb, would the way I did that be fine to do the 1G partition for your steps?

---

### Post by Jonathan Precise on 2013-09-12
Yes it is fine.

---

### Post by oldfred on 2013-09-12
Issue is with new very large hard drives, I normally suggest 10 to 25GB for / (root) anyway and rest of drive as /home. But a separate /boot at beginning of drive also works. Grub and kernels must be nearer start of drive.

But issue has been more older BIOS and often USB systems directly booting. New UEFI based systems have not shown issue when UEFI booting.

Do you have settings in UEFI menu to make it boot only with Legacy/BIOS/CSM and not with UEFI?

---

### Post by ryan29 on 2013-09-13
I am not able to check the "Separate /boot partition" in Boot Repair. It is low lighted and not able to be selected. The partition i made is called /dev/sda3 ext4 1000mb, is that right?

---

### Post by oldfred on 2013-09-13
You have to install with the separate /boot, although once I moved boot files from my install to a /boot and was able to boot. But 5 minutes later realized I did not want a separate /boot, so I moved files back to / (root).
If moving files use cp with -a or rsync with parameters to preserve ownership & permissions as they are vital.

---

### Post by Jonathan Precise on 2013-09-13
> **ryan29 said:**
> I am not able to check the "Separate /boot partition" in Boot Repair. It is low lighted and not able to be selected. The partition i made is called /dev/sda3 ext4 1000mb, is that right?

Do not run boot-repair yet.
Find _*the-name-of-the-device-where-ubuntu-is-installed*_ in GParted.
Run:

```
sudo mkdir /target-root-directory
sudo mkdir /target-boot-directory
sudo mount /dev/_*the-name-of-the-device-where-ubuntu-is-installed*_ /target-root-directory
sudo mount /dev/sda3 /target-boot-directory
mv /target-root-directory/boot/* /target-boot-directory
sudo umount /dev/sda3
sudo umount /dev/_*the-name-of-the-device-where-ubuntu-is-installed*_
```

Run boot-repair again as mentioned (with seperate /boot) and select _*the-name-of-the-device-where-ubuntu-is-installed*_. Post any errors here with code tags.

---

### Post by ryan29 on 2013-09-13
when I run the terminal and type mv /target-root-directory/boot/* /target-boot-directory

I get this

$ mv /target-root-directory/boot/* /target-boot-directory
mv: cannot create regular file `/target-boot-directory/abi-3.8.0-29-generic': Permission denied
mv: cannot create regular file `/target-boot-directory/abi-3.8.0-30-generic': Permission denied
mv: cannot create regular file `/target-boot-directory/config-3.8.0-29-generic': Permission denied
mv: cannot create regular file `/target-boot-directory/config-3.8.0-30-generic': Permission denied
mv: cannot create directory `/target-boot-directory/grub': Permission denied
mv: cannot create regular file `/target-boot-directory/initrd.img-3.8.0-29-generic': Permission denied
mv: cannot create regular file `/target-boot-directory/initrd.img-3.8.0-30-generic': Permission denied
mv: cannot create regular file `/target-boot-directory/memtest86+.bin': Permission denied
mv: cannot create regular file `/target-boot-directory/memtest86+_multiboot.bin': Permission denied
mv: cannot open `/target-root-directory/boot/System.map-3.8.0-29-generic' for reading: Permission denied
mv: cannot open `/target-root-directory/boot/System.map-3.8.0-30-generic' for reading: Permission denied
mv: cannot create regular file `/target-boot-directory/vmlinuz-3.8.0-29-generic': Permission denied
mv: cannot open `/target-root-directory/boot/vmlinuz-3.8.0-30-generic' for reading: Permission denied

---

### Post by Jonathan Precise on 2013-09-13
Try:

[COLOR=#000000]```
sudo -i mv /target-root-directory/boot/* /target-boot-directory
```

to see if it works.[/COLOR]

---

