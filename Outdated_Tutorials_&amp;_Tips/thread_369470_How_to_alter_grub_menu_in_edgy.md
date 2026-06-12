---
title: "How to alter grub menu in edgy"
date: 2007-02-24
forum: Outdated Tutorials &amp; Tips
---

### Post by mshlin on 2007-02-24
Just listened to tip on how to remove previous kernels from grub menu on linux reality podcast, but i didn't work for me. I,m still learning. I played around with the idea & got it to work for me by doing the following (hope it helps somebody :) ).

How to alter grub menu in edgy

Use the Ctrl-Alt-F1 shortcut keys to switch to the console.

logon in with username & password.

enter

sudo nano /boot/grub/menu.lst

comment out kernel titles you dont want to appear when you boot up in grub

use hash key #

I commented out old kernels

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

#title		Ubuntu, kernel 2.6.17-10-generic
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash
#initrd		/boot/initrd.img-2.6.17-10-generic
#quiet
#savedefault
#boot

#title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro single
#initrd		/boot/initrd.img-2.6.17-10-generic
#boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
boot


Press Ctrl x to exit nano, you will be prompted to save the file, enter y

enter exit 

Use the Ctrl-Alt-F7 shortcut keys,to get back to desktop mode.
reboot & check new grub menu   

I assume you could do the same using the terminal by entering

sudo gedit /boot/grub/menu.lst


found good grub info @

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

main site has some good info for ubuntu newbie

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by bernied on 2007-02-24
Something to keep in mind - when you install a kernel update, which usually happens every few months or even more frequently, all your work will be undone. 

This is because there is a script called update-grub which is run when a new kernel is installed. This script changes all of the menu entries that are inside the area of the menu.lst file that is bounded by:
```
### BEGIN AUTOMAGIC KERNELS LIST
```at the beginning, and
```
### END DEBIAN AUTOMAGIC KERNELS LIST
```at the end. But you can decide exactly how this script operates. The script takes it's commands from the first part of that area, that looks like this:
```
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=b8744f06-3942-4dca-9e0d-1f367aaf1054 ro
# kopt_2_6=root=/dev/hdb1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## [there is more like this]

## ## End Default Options ##
```In this section, anything with only one '#' is actually a command to the update-grub script. Comments in this area have '##'. So all that commented text is telling you what you can do with the options. The options for update-grub that I have set, are:
```
# kopt=root=UUID=b8744f06-3942-4dca-9e0d-1f367aaf1054 ro
# kopt_2_6=root=/dev/hdb1 ro
# groot=(hd1,0)
# alternative=true
# lockalternative=false
# defoptions=quiet splash
# lockold=false
# altoptions=(recovery mode) single
# howmany=2
# memtest86=true
```(Please do not copy and paste these into your own file, by the way, especially not the first one - it refers to a specific partition on a specific disk, mine)

Now I don't actually understand all of those options, but I do know that the 'howmany=2' means that it will only look for my two most-recent kernels and give me menu entries for those, and the 'alternative=true' and 'altoptions=(recovery mode) single' options mean that for each of those two kernels I will get another (alternative) menu entry which will have the same name except that it will have '(alternative)' at the end, and it will be the same as the standard entry except that the 'single' parameter will be passed to the kernel, which tells it to boot in single-user (root) mode.

So you might want to edit this area as well.

But, before you do I suggest you take a copy of the file:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.working
```then if anything goes wrong you can restore it like this:
```
sudo cp /boot/grub/menu.lst.working /boot/grub/menu.lst
```Just remember that if things go wrong after you've installed a new kernel, you should run the update-grub script as well:
```
sudo update-grub
```

I hope this is helpful.

---

### Post by mshlin on 2007-02-27
Thanks for tip bernied. Some good info I didn't know. 
Learning all the time due to brilliant support in the forum.:)

---

