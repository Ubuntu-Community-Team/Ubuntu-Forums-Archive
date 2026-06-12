---
title: "Ubuntu 11.10 boot problem"
date: 2011-11-11
forum: New to Ubuntu
---

### Post by cistun on 2011-11-11
Here the boot info script print of my laptop (Hp pavilion dv8000 EE944AV). There is nothing wrong with the installation of Windows (it's not a dual boot i installed Windows just to see nothing's wrong with the hdd) but when it comes to ubuntu it always gives the same boot problem and busybox starts.I had tried all the stuff written on the net for the last week and nothing's changed. Can anyone help me to understand what's the problem? 

[http://paste.ubuntu.com/735168/](http://paste.ubuntu.com/735168/)

---

### Post by Rubi1200 on 2011-11-11
> Can anyone help me to understand what's the problem? 
Answer = yes

Here is the problem:
> Grub2 (v1.99) is installed in the boot sector of sda1

You need to install GRUB to the MBR of the drive not the partition where Ubuntu is installed.

From a LiveCD, do the following:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```

After the last command has finished, reboot and run the following command:

```
sudo update-grub
```

Let us know how you get on.

---

### Post by cistun on 2011-11-11
After this

sudo grub-install --boot-directory=/mnt/boot /dev/sda

it says

/usr/sbin/grub-setup: error: cannot write to '/dev/sda'

---

### Post by mgmontague on 2011-11-11
I have a Grub problem. I'm receiving a Grub Error whenever I try to boot. I know the problem is the boot path can not be found.
I can not use the Live CD on account this is a mini computer without a CD just USB. I tried a HDD Flash Drive but whenever I try to boot up to it, it starts up but goes back into the hard drive and again, wrong path, no boot. I have a USB DVD drive, and the system will not even recognize the unit.

I have setup boot seq. in bios, and I have used F12 over and over.

Nothing. I now, have a one pound paper weight.

I'm considering using a Kill disk and hopefully wipe everything off of the hard drive. Though, I doubt if this will boot up either.

Any suggestions....?

MG Montague

---

