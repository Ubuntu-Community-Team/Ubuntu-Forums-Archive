---
title: "No High VGA modes for GRUB"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by noorez on 2008-09-25
I wanted to use a higher resolution for grub and the splash screen during startup with GRUB so I followed some online examples to add the VGA option to the kernel parameter. However, when I restarted, GRUB reported that I had given an invalid VGA value. I pressed the enter key to see what was available and only 5 options were presented to me...all at about 80*(20,30,60...). Can anyone tell me what happened?! I know for sure that my screen is capable of 1280x800x32. How would I fix this problem?

---

### Post by Nepherte on 2008-09-25
Put edd=off in the kernel line. For example:
```
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/7724689e-bad7-4a95-b99a-35c517a5b344 ro vga=795 **edd=off**
```

These are the framebuffer resolution settings:
```
#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
```

---

### Post by LowSky on 2008-09-25
there are two programs that can give you better resolutions 

one is called Start-up manager and the other QGrubeditor

both are in synaptic

---

### Post by noorez on 2008-09-25
no go. it didn't work. I got the same error. I've also already tried Startup manager but I'll give the other one a go...

---

### Post by noorez on 2008-09-25
none of the tools worked.

---

### Post by Nepherte on 2008-09-25
What's the exact error message? Perhaps this works:
```
vga=normal
```

---

### Post by noorez on 2008-09-25
Here is what the error message is:

Undefined video mode number: 31b
Press <ENTER> to see video modes available, <SPACE> to continue or wait 30 sec

Mode: COL*ROWS:
0  0F00 80*25 VGA
1  0F01 80*50 VGA
2  0F02 80*43 VGA
3  0F03 80*28 VGA
4  0F05 80*30 VGA
5  0F06 80*34 VGA
6  0F07 80*60 VGA

---

### Post by Nepherte on 2008-09-26
So not this one?
```
Probing EDD (edd=off to disable)
Undefined video mode number: 31b
Press <ENTER> to see video modes available, <SPACE> to continue or wait 30 sec
```

That's the one I had, but if it's not with edd, I don't know of a solution for your problem.

---

### Post by icanfly0307 on 2009-02-06
Sorry for waking up an old thread but did you guys find the solution to this problem, yet? I have the same error.

---

### Post by unutbu on 2009-02-06
When you press Enter and see this:

```
Mode: COL*ROWS:
0 0F00 80*25 VGA
1 0F01 80*50 VGA
2 0F02 80*43 VGA
3 0F03 80*28 VGA
4 0F05 80*30 VGA
5 0F06 80*34 VGA
6 0F07 80*60 VGA 
```

are any of these modes acceptable to you? If so, we can edit your GRUB menu.lst to make it the default option. If not, it appears according to grahamilton817 ([http://ubuntuforums.org/showpost.php?p=5752866&postcount=1057](http://ubuntuforums.org/showpost.php?p=5752866&postcount=1057)) that you need to compile a new kernel to get high(er) vga modes.

---

### Post by icanfly0307 on 2009-02-06
No, none of these modes are acceptable. They're way too small. I just need the boot text that's scrolling by to stretch in from the entire screen

---

### Post by prescor on 2009-12-28
I'm also looking for a resolution to this.  I find lots of dated threads that refer to a menu.lst file, but 9.10 doesn't have one.  I've tried editing /etc/default/grub with 'vga=795' (the native resolution of the display I'm using) and I still can't see anything.  This display is incapable of displaying 640x480.

---

