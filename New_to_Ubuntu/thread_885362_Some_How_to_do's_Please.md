---
title: "Some How to do's Please"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by audreymac on 2008-08-10
How to
show Ubunto and Windows on initial loading - so that its possible to just click on either to connect.:confused:

---

### Post by cdtech on 2008-08-10
How are you booting now? Do you boot into windows or ubuntu?

---

### Post by Elfy on 2008-08-10
You probably just need to edit the menu list and stop it being hidden - is it there if you press esc.

---

### Post by audreymac on 2008-08-10
Start computer - black screen (bios?) choose windows or ubuntu - enter...
I installed from Ubuntu 8.04 from disk.
Need to simplify this, as other user on computer won't understand the initial setup.....

---

### Post by audreymac on 2008-08-10
I will try menu list at bottom of page then.
Thanks for info.
amc

---

### Post by Elfy on 2008-08-10
There is a clickable menu - I can't remember of the top of my head what it is though - I'll try and remember. Though I don't quite know how much simpler it can be - or do you mean that you only want 1 ubuntu visible?

---

### Post by Bradtek on 2008-08-10
> **audreymac said:**
> Start computer - black screen (bios?) choose windows or ubuntu - enter...
I installed from Ubuntu 8.04 from disk.
Need to simplify this, as other user on computer won't understand the initial setup.....

If pressing the "Enter Key" is not simple enough for the "other user"
What hope does has this "other user" have of doing  anything once loaded ?

Or am I misunderstanding your post ?

---

### Post by audreymac on 2008-08-10
Not much hope - other is absolutely technophobic, but likes some light browsing.
So a nice SIMPLE inital page is whats needed.....:)

---

### Post by Elfy on 2008-08-10
You could remove the old kernels and recovery - but and it's quite a big but - if you have a problem you'll not be able to get in to sort it without editing the menu list from the livecd.

You could move the windows option above the automagic debian line and it should stay there - then the 'other' will only need to choose between top 2 - also you could have it default to the one the 'other' uses and keep the hard stuff for you :D

If you need any help with that - open aterminal, run command and post the whole of the output here - please use code tags at beginning and end of output - # in toolbar or [BB code]("http://ubuntuforums.org/misc.php?do=bbcode")

---

### Post by ugm6hr on 2008-08-10
> **audreymac said:**
> Not much hope - other is absolutely technophobic, but likes some light browsing.
So a nice SIMPLE inital page is whats needed.....:)

If so - they should probably only learn to use 1 OS rather than 2.

Set whichever you want as the default for them to load.  That way, no clicking required.

---

### Post by audreymac on 2008-08-10
How to: set as Default?

---

### Post by cdtech on 2008-08-10
You would need to edit the /boot/grub/menu.lst and change the line that says default 0 to the order number listed in menu.lst:
```
sudo gedit /boot/grub/menu.lst
```
Change the line:
```
default		0
```
To the OS list number:
```

**0)** title		8.04.1, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-17-generic root=UUID=41d95d32-e6bf-418b-b3fe-278d0c7ba5e1 ro quiet vga=792
initrd		/initrd.img-2.6.24-17-generic
quiet

**1)** title		8.04.1, kernel 2.6.24-17-generic (text mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-17-generic root=UUID=41d95d32-e6bf-418b-b3fe-278d0c7ba5e1 ro vga=792 init 3
initrd		/initrd.img-2.6.24-17-generic
[B]
2)[/B] title		8.04.1, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-17-generic root=UUID=41d95d32-e6bf-418b-b3fe-278d0c7ba5e1 ro init S
initrd		/initrd.img-2.6.24-17-generic
```

---

### Post by Elfy on 2008-08-10
You need to change the default - open the menu list to edit it 

```
gksudo gedit /boot/grub/menu.lst
```

Change the default to correspond to the line you want as default - be aware that grub counts from 0 - If for instance I set my default to 7 it would try to boot the title in red.

If you want to default to windows and it's at the very end, when you get kernel updates you will need to change it - it might be better for you to, in that case, to move it above the ### BEGIN AUTOMAGIC KERNELS LIST
 line and set it to 0 - or at least I think that should work - never done it myself.


```
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-20-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=ccf8f1c4-97d0-4544-a0ee-04088d5d67a9 ro quiet vga=771 splash
initrd		/boot/initrd.img-2.6.24-20-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-20-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=ccf8f1c4-97d0-4544-a0ee-04088d5d67a9 ro single
initrd		/boot/initrd.img-2.6.24-20-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ccf8f1c4-97d0-4544-a0ee-04088d5d67a9 ro quiet vga=771 splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ccf8f1c4-97d0-4544-a0ee-04088d5d67a9 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=ccf8f1c4-97d0-4544-a0ee-04088d5d67a9 ro quiet vga=771 splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=ccf8f1c4-97d0-4544-a0ee-04088d5d67a9 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

[COLOR="Red"]title[/COLOR] Intrepid Boots

title		Ubuntu intrepid (development branch), kernel 2.6.26-5-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.26-5-generic root=UUID=c06db3c6-4472-48cf-ac34-2f034a2531ed ro quiet splash 
initrd		/boot/initrd.img-2.6.26-5-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.26-5-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.26-5-generic root=UUID=c06db3c6-4472-48cf-ac34-2f034a2531ed ro  single
initrd		/boot/initrd.img-2.6.26-5-generic


```

---

### Post by audreymac on 2008-08-10
A lot to digest, for now - as a beginner.
Thanks again.

---

### Post by Elfy on 2008-08-10
Indeed it can be - I know how you feel, if you think that you're getting stuck with the problem, post back.

If you are not sure what to change post your menu list here - run this command and post the whole output

```
cat /boot/grub/menu.lst
```

---

