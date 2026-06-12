---
title: "Changing entries in GRUB"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by Anonono on 2008-10-03
Right now, I have five entries in GRUB. The three normal Ubuntu ones, one that activates a recovery partition that will wipe my HDD, and one for XP.
How can I remove the recovery one? And would it be okay to remove the two extra Ubuntu ones?

---

### Post by adult swim on 2008-10-03
hit alt-f2 and then run ```
gksudo gedit /boot/grub/menu.lst
``` that will bring up your grub menu file.  if you scroll down you will see the options that you are presented with.  you can delete the entries that you are not using.  personally i would delete the third ubuntu entry, then comment out the second one (commenting out is placing a # at the beginning of every line of the entry) so you can easily boot it if you ever brick your current ubuntu.
an example 
```
title		Ubuntu intrepid (development branch), kernel 2.6.27-4-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=798646bd-85bf-4ead-9a80-4eda9bb1f8e7 ro quiet splash        ----you keep this one
initrd		/boot/initrd.img-2.6.27-4-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.27-4-generic (recovery mode)             ----you want to keep the recovery mode
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=798646bd-85bf-4ead-9a80-4eda9bb1f8e7 ro  single
initrd		/boot/initrd.img-2.6.27-4-generic


#title		Ubuntu intrepid (development branch), kernel 2.6.24-19-generic                            ----see how this is a different kernel
#root		(hd0,3)                                                                                   ---- you can comment out like this
#kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=798646bd-85bf-4ead-9a80-4eda9bb1f8e7 ro  single
#initrd		/boot/initrd.img-2.6.24-19-generic
#quiet

#title		Ubuntu intrepid (development branch), kernel 2.6.24-19-generic (recovery mode)
#root		(hd0,3)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=798646bd-85bf-4ead-9a80-4eda9bb1f8e7 ro  single
#initrd		/boot/initrd.img-2.6.24-19-generic


```
and you could delete the last ubuntu entry off of the list.

---

### Post by Shazaam on 2008-10-04
What you can do is edit menu.lst (Lst) and comment out (#) the unwanted entries. This does NOT uninstall/remove any files. Instead of this...
```
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda9 ro single
initrd		/boot/initrd.img-2.6.24-16-generic
```
you would have this...
```
#title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
#root		(hd0,8)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda9 ro single
#initrd		/boot/initrd.img-2.6.24-16-generic
```
Open terminal and enter this command...
```
gksudo gedit /boot/grub/menu.lst
```
This code allows you to edit menu.lst as root (gksudo). Make sure you comment out the correct entries; if you make a mistake and cannot boot you can use the Ubuntu livecd to fix it.

edit: adult swim beat me to it. :)

---

### Post by drs305 on 2008-10-04
If you would prefer using a gui app to edit your menu.lst I highly recommend StartUp-Manager. I originally wrote the tutorial for dealing with the extra kernels that are displayed after an update, so it covers this as well as how to set the display timeout, default OS, etc.

It also discusses why it may be better to uninstall the old kernels than remove them from menu.lst (and when/how to do it).

Here is the link:
[StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by mcduck on 2008-10-04
I'd recommend uninstalling the old kernels. Leave one, if you want, but the others are definitely just waste of disk space.

To remove them you can, for example, search for "linux" in package name with Synaptic to find the linux images, headers & restricted modules packages. Then simply right-click and select the old versions to be removed.

I usually uninstall the old kernels a couple of days after upgrading to a new kernel. I've never run into any troubles after first cnfirming that the latest kernels works fine. Of course you can play safe and leave the last kernel installed, just to be very safe, but I definitely can't imagine any situation where not only the latest kernel would fail, but also your previous kernel, which worked just fine before, would suddenly refuse to run forcing you to use even older version.. So I can't really see any reason in keeping more than one old kernel available.

Still, if you want to kep them all installed but don't want to show them in the Grub menu the menu.list file has a setting for the number of kernels to show in menu. Just change the number to whatever you want..

---

