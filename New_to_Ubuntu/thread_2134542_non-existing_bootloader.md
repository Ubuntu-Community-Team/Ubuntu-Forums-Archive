---
title: "non-existing bootloader"
date: 2013-04-11
forum: New to Ubuntu
---

### Post by LinuxUser666 on 2013-04-11
Hello fellow GNU/Linux users.
I am running Ubuntu 12.04 LTS with Unity. I have also installed Back Track 5 r3 as a dual boot to Ubuntu.
My problem begins at boot, it simply does not show me anything, by that I mean some bootloader where I can pick which OS i wanna boot. So what do i need to do to make this thing working?

---

### Post by arpanaut on 2013-04-11
Here ya go:
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by Bashing-om on 2013-04-11
LinuxUser666; Hi !

Try this to install grub for ubuntu:
You will need a LiveCD/USB. Boot into the Live Environment and go to: Key combo ctl+alt+t to get a terminal.
```
sudo fdsik -l  ## to identify the root partition ("*")
sudo mount /dev/sda1 /mnt ##Mount your OS partition:
```
Next, install GRUB2:
```
sudo grub-install --root-directory=/mnt /dev/sda
```
(Don't put a partition number in this command, just the HDD location a, b, etc. from "fdisk "*")
Now unmount:
```
sudo umount /mnt
```
Reboot and I expect that ubuntu boots:
Now we need to pick up Back Track;
ctl+alt+t -> terminal
```
sudo update-grub
```should chainload Back Track onto the boot loader.
Reboot.[INDENT=3]workie now ?

[/INDENT]

---

### Post by LinuxUser666 on 2013-04-11
Thank you Bashing-om, your advice helped me quite a lot, now I have a bootloader and all works.  This forum, still beeing awesome.

---

### Post by Bashing-om on 2013-04-11
LinuxUser666; Hey Great.

Pleased you are up and running !
Please mark this thread as solved, to aid all ( keeps our forum tidy too !).

> Interim method:
Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.[INDENT=2]
ubuntu, all for 1 and one for all
[/INDENT]

---

