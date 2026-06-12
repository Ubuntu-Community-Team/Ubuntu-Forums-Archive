---
title: "[SOLVED] how to turn off verbal boot?"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by grikdog on 2008-08-26
I'm not when this started, but Ubuntu has begun booting in verbal mode (the way Slackware used to).  Previously, boots were quiet.  Maybe this is because I allowed the last major update to change the Grub file (??).

What do I need to change to go back to the visual boot?  What file do I look at to see (or not see) all the running commentary?

Thanks!
d

---

### Post by Separ on 2008-08-26
You mean verbose?

Post the output of
```
cat /boot/grub/menu.lst
```

---

### Post by coffeecat on 2008-08-26
Are you getting the Ubuntu splash screen where the orange bar sweeps back and forth, but when you get to the part where the progress bar should fill from left to right, you get a verbose boot? And is there any way the UUID of your swap partition could have changed - such as, have you installed another distro to another partition or have you resized swap?

If so, have a look at my first post (#5) in [this thread]("http://ubuntuforums.org/showthread.php?t=857565"). The fix is there.

If not, go with Separ.

---

### Post by grikdog on 2008-08-26
That's exactly the case!  I resized my linux-swap.  No joy on the blkid, initramfs, etc., however.

I finally got my UUID's in the various files synchronized by DELETING my swap partition (which was inactive anyway), recreating it, getting its UUID by running 'sudo vol_id /dev/sda2' and manually editing /etc/fstab and /etc/initramfs-tools/conf.d/resume to match the output of 'sudo blkid -c /dev/null'...

Now what happens when I boot is, I still get exactly the same behavior (sweeping orange bar, then it switches over to "Reading files needed to boot" and proceeds verbosely from that point.

So maybe the issue is menu.lst after all?

menu.lst follows:
-----------------

default 0
fallback 1
timeout 5
hiddenmenu

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=1a276280-36dc-401b-ba86-99998b40c4d8 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=1a276280-36dc-401b-ba86-99998b40c4d8 ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd0,2)
kernel /boot/memtest86+.bin
quiet
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=1a276280-36dc-401b-ba86-99998b40c4d8 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=1a276280-36dc-401b-ba86-99998b40c4d8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=1a276280-36dc-401b-ba86-99998b40c4d8 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1a276280-36dc-401b-ba86-99998b40c4d8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1a276280-36dc-401b-ba86-99998b40c4d8 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1a276280-36dc-401b-ba86-99998b40c4d8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1a276280-36dc-401b-ba86-99998b40c4d8 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by coffeecat on 2008-08-26
> **grikdog said:**
> That's exactly the case!  I resized my linux-swap.  No joy on the blkid, initramfs, etc., however.

I finally got my UUID's in the various files synchronized by DELETING my swap partition (which was inactive anyway), recreating it, getting its UUID by running 'sudo vol_id /dev/sda2' and manually editing /etc/fstab and /etc/initramfs-tools/conf.d/resume to match the output of 'sudo blkid -c /dev/null'...

Now what happens when I boot is, I still get exactly the same behavior (sweeping orange bar, then it switches over to "Reading files needed to boot" and proceeds verbosely from that point.


But after editing /etc/initramfs-tools/conf.d/resume, you **must** run 'sudo update-initramfs -u' to generate a new initrd image otherwise usplash won't work.

---

### Post by grikdog on 2008-08-26
yes, did that.  no joy

---

### Post by grikdog on 2008-08-26
I think I see the problem.  After doing all of coffeecat's UUID synch-ing, when I run 'sudo update-initramfs -u' to generate a new initrd image, it makes initrd.img-2.6.24-21-generic, however grub thinks initrd.img-2.6.24-16-generic is the default.

This is way over my head.  How do I set grub to boot 21 and not 16?
TIA,
d

---

### Post by grikdog on 2008-08-26
> **grikdog said:**
> I think I see the problem.  After doing all of coffeecat's UUID synch-ing, when I run 'sudo update-initramfs -u' to generate a new initrd image, it makes initrd.img-2.6.24-21-generic, however grub thinks initrd.img-2.6.24-16-generic is the default.

This is way over my head.  How do I set grub to boot 21 and not 16?
TIA,
d

Ha! Got it!  The trick is to use QGrubEditor and simply move the correct version to the top of the list!  That makes it the default, and all the work CoffeeCat did immediately pays off!

Thanks, thanks, thanks!
d

---

### Post by coffeecat on 2008-08-26
> **grikdog said:**
> This is way over my head.  How do I set grub to boot 21 and not 16?
TIA,
d

```
gksudo gedit /boot/grub/menu.lst
```Go to the beginning of the file. See the 'hiddenmenu' line? Put a hash symbol in front so that it looks like:

```
#hiddenmenu
```That will make the grub menu appear so that you can select the kernel you want. But first - change 'timeout 5' to:

```
timeout 10
```5 seconds is too short. Now save the file and exit gedit.

**[COLOR=red]HEALTH WARNING - Do NOT use the 2.6.24-21-generic kernel.[/COLOR]** You have the Proposed Updates repository enabled, haven't you? [-X The -21 kernel will break your system, upset old ladies and cause global warming. [Read this]("https://help.ubuntu.com/community/UbuntuUpdates").

Boot into the -19 kernel, and run the instructions I suggested earlier and your usplash should work.

But then you need to do something about your menu.lst (which is a bit odd) and the Proposed repository. Let's do one thing at a time though.

**Edit:** I see you managed to sort out menu.lst while I was posting. But use the -21 kernel at your own risk. I strongly advise you to disable the proposed updates repository

---

### Post by -Zeus- on 2008-08-26
-21 works fine, I use it.  if you want slightly unstable, go *-25* :-P

---

### Post by coffeecat on 2008-08-26
> **-Zeus- said:**
> -21 works fine, I use it.  if you want slightly unstable, go *-25* :-P

OK, fair enough - it was the -20 kernel that was the real disaster, but there are some threads from people who had significant problems with the -21 kernel. I just wanted the OP to read the link about the proposed updates repo. If people want to help with testing, that's fine, but if they want a stable system, it's best avoided.

---

### Post by -Zeus- on 2008-08-26
hehe fair enough.  @OP: while disabling proposed make sure that you haven't enabled hardy-backports

---

### Post by grikdog on 2008-08-26
> **-Zeus- said:**
> hehe fair enough.  @OP: while disabling proposed make sure that you haven't enabled hardy-backports

Ok, I have to ask:  How do I disable proposed?  How do I disable hardy-backports?  What IS "proposed"?  What IS "hardy-backports"?

I have to ask, because TTBOMK I never enabled anything like that, at least not intentionally.  I was looking at the Intrepid distro iso.  Did that mess it up (it gave me the option to run package installer on the DVD)?

I'm not actually having any problems since this afternoon.

---

### Post by grikdog on 2008-08-26
> **coffeecat said:**
> ```
gksudo gedit /boot/grub/menu.lst
```Go to the beginning of the file. See the 'hiddenmenu' line? Put a hash symbol in front so that it looks like:

```
#hiddenmenu
```That will make the grub menu appear so that you can select the kernel you want. But first - change 'timeout 5' to:

```
timeout 10
```5 seconds is too short. Now save the file and exit gedit.

**[COLOR=red]HEALTH WARNING - Do NOT use the 2.6.24-21-generic kernel.[/COLOR]** You have the Proposed Updates repository enabled, haven't you? [-X The -21 kernel will break your system, upset old ladies and cause global warming. [Read this]("https://help.ubuntu.com/community/UbuntuUpdates").

Boot into the -19 kernel, and run the instructions I suggested earlier and your usplash should work.

But then you need to do something about your menu.lst (which is a bit odd) and the Proposed repository. Let's do one thing at a time though.

**Edit:** I see you managed to sort out menu.lst while I was posting. But use the -21 kernel at your own risk. I strongly advise you to disable the proposed updates repository

Thanks for the warnings!  Yes, I found "proposed" and "hardy backports" in the System Sources utility, and YES, I did it to myself with foolhardy tweaking.  Hence, MUNG Until No Good.  Yay me.

Also found the update-initramfs -k switch and set up for 19, not 21.  So everything is now working as it should... (heh)... Looks ok, anyway, and the verbose boot has gone away and the occasion fsck appears in orange, so perfect :)

---

