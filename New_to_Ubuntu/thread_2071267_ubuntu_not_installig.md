---
title: "ubuntu not installig"
date: 2012-10-15
forum: New to Ubuntu
---

### Post by sparshadotel on 2012-10-15
i am a newbie in ubuntu and am having a problem while installing it. installing with wubi, it says no root system is defined and if i try it using live boot it shows my hard drive as an entire free space with no partition while in actual, i have 3 partitions. i even deleted all partitions and created new partitions but it just doesnt work. 
help me please

---

### Post by kailashk on 2012-10-15
Hi, 

WUBI, afaik is for for installing Ubuntu alongside a pre-existing Windows installation.

For regular installs, you should choose "install Ubuntu" as the option if you're going for a dedicated linux machine.

Which one are you aiming for?

K.

---

### Post by Wim Sturkenboom on 2012-10-15
> **kailashk said:**
> 
WUBI, afaik is for for installing Ubuntu alongside a pre-existing Windows installation.
make that '**inside** a pre-existing Windows installation' ;)

---

### Post by sparshadotel on 2012-10-15
i am aiming to boot linux inside windows (without the grub i mean)

---

### Post by newb85 on 2012-10-15
> **sparshadotel said:**
> i am aiming to boot linux inside windows (without the grub i mean)

Are you doing this just to avoid Grub?  Or are you looking to run Ubuntu inside a full Windows environment?

If you want it inside a full Windows environment, then neither the Live CD nor the Wubi install will achieve what you want.  Instead, you would need to install Ubuntu on a virtual machine (VM) inside Windows using a VM client, like VirtualBox.

---

### Post by Wim Sturkenboom on 2012-10-15
> **sparshadotel said:**
> i am aiming to boot linux inside windows (without the grub i mean)
This might sound silly, but is Windows installed (just asking because you state that you deleted all partitions)? wubi, to my knowledge, uses a file inside windows (so does not use partitions)

I'm not familiar with wubi, so can't really advise further.

---

### Post by audiomick on 2012-10-15
> **Wim Sturkenboom said:**
> This might sound silly, but is Windows installed (just asking because you state that you deleted all partitions)? wubi, to my knowledge, uses a file inside windows (so does not use partitions)

I'm not familiar with wubi, so can't really advise further.

+1 that man. I haven't done a WUBI install, but from what the OP has written, it does sound like there is some confusion happening there regarding which type of installation is happening.

@sparshadotel: just by the way, from what I have read, if you do a Wubi install, you still see a grub menu at boot, just like when you do a proper dual boot install.

---

### Post by Wim Sturkenboom on 2012-10-15
> **audiomick said:**
> @sparshadotel: just by the way, from what I have read, if you do a Wubi install, you still see a grub menu at boot, just like when you do a proper dual boot install.I don't think wubi gives you a grub menu; a menu, yes, but from Windows (as far as I know).

---

### Post by audiomick on 2012-10-15
> **Wim Sturkenboom said:**
> I don't think wubi gives you a grub menu; a menu, yes, but from Windows (as far as I know).

Ah, it seems you are right. This is from the Wubi installation guide (point 10)
[IMG]https://help.ubuntu.com/community/Wubi?action=AttachFile&do=get&target=Wubi1.png[/IMG]

[https://help.ubuntu.com/community/Wubi]("https://help.ubuntu.com/community/Wubi")

---

### Post by sparshadotel on 2012-10-16
its not what i meant. i want to install ubuntu side by side with windows . not inside windows. i.e. no vmware or any vrtual workstations

---

### Post by sparshadotel on 2012-10-16
i have a screenshot in my attachment while doing a live boot and installing ubuntu
(mind you that i already have installed windows 8 and have 3 partitions)
and it still shows an entire free space.no partitions. what seems to be the problem here?

---

### Post by newb85 on 2012-10-16
How many hard drives do you have?  It's only showing one (sda) with 500GB in the partitioning pane, but then, under device for boot loader install, you have a second one (sdb) selected.

---

### Post by sparshadotel on 2012-10-16
i only have one hdd and its shown completely while in real its not

---

### Post by Wim Sturkenboom on 2012-10-16
I doubt that there are partitions on that HD. You can verify using the liveCD or liveUSB by running the following command

```

sudo fdisk -l

```
Note that it's a lowercase L at the end of the command. Post the output here (preferable between code tags).

It's quite confusing if you want Ubuntu alongside Windows (dual boot with grub) or Ubuntu inside Windows (wubi install); it's clear that you don't want a virtual machine.

In any case, I suggest that you install Windows first. The last Windows that I installed myself was WinXP and it offered the option to partition. Use that if you want a dual boot with grub and install Windows. Next install Ubuntu (either inside Windows or next to Windows).

PS /dev/sdb might be a memory stick (or the live USB).

---

### Post by sparshadotel on 2012-10-17
here's the problem ,while scanning the disks partitions are seen. but why are they not whle installing ubuntu as i showed it to you .
and any type of installation works for me(ie with wubi or grub)

---

### Post by Wim Sturkenboom on 2012-10-17
OK. you were right regarding the partitions. I don't have the solution; the only thing that strikes me is that it's GPT, but I thought that gparted could handle that.

---

### Post by sparshadotel on 2012-10-17
can you suggest me to anyone?

---

### Post by Linux_junkie on 2012-10-17
I have noticed that all partitions are set to NTFS. Using GParted (from the liveCD) replace at least one of the NTFS partitions (that's not being used for anything) to Linux partition (ext2/3/4).

---

### Post by Wim Sturkenboom on 2012-10-17
> **Linux_junkie said:**
> I have noticed that all partitions are set to NTFS. Using GParted (from the liveCD) replace at least one of the NTFS partitions (that's not being used for anything) to Linux partition (ext2/3/4).Assuming the second screenshot in post #15 is gparted, it does not see the partitions.

---

### Post by gerrman97 on 2012-10-17
you have to create the partitions from the install.

---

### Post by newb85 on 2012-10-17
Try this:
Instead of going straight to the installer, hit "Try Ubuntu".  In the Software Center, Edit > Software Sources and enable the Multiverse.  Then install gpart.  (It's an add-on for gparted that can assist in identifying partitions.)  Then run the installer.

---

