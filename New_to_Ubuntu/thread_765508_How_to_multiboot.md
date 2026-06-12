---
title: "How to multiboot"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by RonStordahl on 2008-04-24
I have a 640 GB drive which I would like to set up to multiboot a number of linux distribution starting with Ubuntu 8.04, and adding perhaps 3 more distributions.

During the Ubuntu install process I selected manual partitioning and set up a 100 MB partition for it, and did a successfuly install.

Then I tried a new install of PCLinuxOS.  It offered a manual partition option which I chose and I created another 100 MB partition and completed the install.

However when I boot it boots only into Ubuntu.  If while booting I hit esc it does give me a menu, but only of Ubuntu things, no sign of PCLinuxOS.

So I have tried, but obviously I don't know what I am doing.

Is there a step by step explanation somewhere of the proper procedure?

Ron

---

### Post by 1440 on 2008-04-24
There are countless howto's on how to do this you can find using Google:

[http://www.google.com/search?q=multi+booting+multiple+linux+os](http://www.google.com/search?q=multi+booting+multiple+linux+os)

Or some other keywords like the ones I used :)

---

### Post by Paqman on 2008-04-24
Sounds like PCLOS didn't set up the GRUB bootloader properly. Both Ubuntu and PCLOS will have a file at /boot/grub/menu.lst which lays out the GRUB config.

If you installed PCLOS second it should have noticed Ubuntu and written a menu.lst file that gives both as options. The Ubuntu one won't know about PCLOS (coz it wasn't there when Ubuntu installed)

If that's the case you can sort it two different ways.

1) Copy the PCLOS menu.lst file over to Ubuntu. Since GRUB is checking the Ubuntu parition to find menu.lst you should get the full list when you boot

2) Alter GRUB to look at the menu.lst on the PCLOS parition. That's pretty simple to do:
```

grub
root (hd0,1)
setup (hd0)

```
Would set up GRUB to look at the second partition on the drive. For other parrition numbers change (hd0,1) to the right number. GRUB starts counting from 0, so sda3 would be hd(0,2)

---

