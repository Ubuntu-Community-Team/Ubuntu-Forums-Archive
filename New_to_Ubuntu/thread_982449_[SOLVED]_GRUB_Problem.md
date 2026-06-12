---
title: "[SOLVED] GRUB Problem"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by CJ Master on 2008-11-14
Howdy!

Well I love ubuntu, and decided to try fluxbuntu because it sounded a lot faster....

Well I didn't care for it too much so I went back to normal ubuntu.

The problem? Well if I just turn on my computer and do nothing, it'll automatically boot to fluxbuntu, but i want it too boot to ubuntu here.

oh yes, btw I don't mind uninstalling fluxbuntu, i just don't know how. And yes, I've tried startup-manager, but it still doesn't want to boot straight here.

---

### Post by MasterSander on 2008-11-14
1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,4)", or wherever your /boot is located (my /boot is at /dev/sda5, the same as my root dir, which translates to hd0,4 for grub).
5. Type "setup (hd0)", or whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

---

### Post by CJ Master on 2008-11-14
1) Does it have to be from the live cd? 2) If so, does it have to be ubunbu live cd or fluxbuntu?

---

### Post by adult swim on 2008-11-14
step 3.5) find /boot/grub/stage1

that will show you what to type in for step 4

---

### Post by epswinde on 2008-11-14
Before you go monkeying around with grub (not something I recommend)-- are you sure its a boot loader problem?  Did you install ubuntu from a live-cd or just use the package ubuntu-desktop?

---

### Post by Duck2006 on 2008-11-14
Some info on grub.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by CJ Master on 2008-11-14
> **epswinde said:**
> Before you go monkeying around with grub (not something I recommend)-- are you sure its a boot loader problem?  Did you install ubuntu from a live-cd or just use the package ubuntu-desktop?

I installed ubuntu first, from a live cd yea.

---

### Post by epswinde on 2008-11-14
> **CJ Master said:**
> I installed ubuntu first, from a live cd yea.

So do you have both gnome and fluxbox installed on the same root file system?  or do you have two different instances of linux (one ubuntu, one fluxbuntu) with different root partitions?

Because if you've got the second case, then you'll need to configure grub.  If you've got the first case, then you just need to just select a different session at the login screen in fluxbuntu.

---

### Post by CJ Master on 2008-11-15
> **epswinde said:**
> So do you have both gnome and fluxbox installed on the same root file system?  or do you have two different instances of linux (one ubuntu, one fluxbuntu) with different root partitions?

Because if you've got the second case, then you'll need to configure grub.  If you've got the first case, then you just need to just select a different session at the login screen in fluxbuntu.

Well, quite honestly, I don't know. :P How do i find out?

---

### Post by adult swim on 2008-11-15
post the output of ```
sudo fdisk -l
```

---

### Post by CJ Master on 2008-11-15
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38ef9d17

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       16593   133283241   83  Linux
/dev/sda2           23685       24321     5116702+   5  Extended
/dev/sda3   *       16594       23684    56958457+  83  Linux
/dev/sda5           23993       24321     2642661   82  Linux swap / Solaris
/dev/sda6           23685       23992     2473947   82  Linux swap / Solaris

Partition table entries are not in disk order
cjmaster@cjmaster-desktop:~$

---

### Post by adult swim on 2008-11-15
have you ever partitioned your hard drive for anything?

---

### Post by CJ Master on 2008-11-15
Yea, I origionally had a partition of windows and ubuntu, I wiped out windows though, forgot how.

And I assume that fluxbuntu and ubuntu is a partition?

---

### Post by caljohnsmith on 2008-11-15
I see you have two linux partitions, sda1 (~133 GB) and sda3 (~57 GB). Do you know which is the Fluxbuntu partition? One way you can find out which partition is controlling Grub in the MBR (Master Boot Record) is with:
```
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
If that returns "ff00", then sda1 controls the MBR, but if you get "ff02", then sda3 is in control of the MBR. Since you want your original Ubuntu to have control of the MBR again, just do:
```
sudo grub
grub> root (hdX,Y)
```
Where (hdX,Y) should be (hd0,2) if you got "ff00" above, or it should be (hd0,0) if you got "ff02" above, and then continue with:
```
grub> setup (hd0)
grub> quit
```
Please post the output of all the above commands, reboot, and let me know if you get your original Ubuntu Grub menu back. If not, let me know what problems you run into. :)

---

### Post by CJ Master on 2008-11-16
Thanks for all your help, but I just did a clean install using all the hd space anyways, so problem solved. :P

---

