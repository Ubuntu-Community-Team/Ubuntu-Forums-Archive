---
title: "Can't mount my ssd."
date: 2017-03-29
forum: New to Ubuntu
---

### Post by gooeysan on 2017-03-29
I was working on some files in my SD card and i downloaded gparted for formatting the mentioned card. When i restarted my laptop to boot Ubuntu 16.04 I only got "grub rescue>" thing. Since I have some highly important files on the drive that i can't lose, i made a live USB of Ubuntu 16.04 and tried to access it that way and only got this:
```
Error mounting /dev/sda1 at /media/ubuntu/0de9f123-f136-497b-a7ca-87b294e540f6: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sda1" "/media/ubuntu/0de9f123-f136-497b-a7ca-87b294e540f6"' exited with non-zero exit status 32: mount: mount /dev/sda1 on /media/ubuntu/0de9f123-f136-497b-a7ca-87b294e540f6 failed: Structure needs cleaning
```
I guess you can call this a cry for help.

---

### Post by oldfred on 2017-03-29
Is sda1 your SD card or an internal drive. Or is SD card your drive(if one of the mini-systems)?

Do not know what structure means.

 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

---

### Post by gooeysan on 2017-03-30
My SD card doesn't really have anything to do with the internal drive. My internal ssd got corrupted or something like that after me working on the sd card, formatting it and rebooting. sda1 is the internal ssd.
Edit: Mentioned SD card because that was the last thing i did before restarting.

---

