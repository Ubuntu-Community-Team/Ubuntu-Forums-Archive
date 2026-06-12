---
title: "[SOLVED] Grub Chain loader, is the boot line needed."
date: 2008-07-17
forum: New to Ubuntu
---

### Post by philinux on 2008-07-17
```
title Another Linux Installed on Hard Drive 2.
root (hd1,0)
chainloader +1
```

This is how I'm booting my second hardrive.

In a grub guide it shows an extra line, after chainloader, which just says

boot

It doesn't seem to be affecting my chainloader, what does it do?

---

### Post by ibuclaw on 2008-07-17
> **boot**
Command: boot

Boot the OS/chain-loader which has been loaded. Only necessary if running the fully interactive command-line (it is implicit at the end of a menu entry). 

Here's my source:
[http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_4.html](http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_4.html)

and here too:
[http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_12.html#SEC64](http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_12.html#SEC64)

Regards
Iain

---

### Post by philinux on 2008-07-17
I'm not thick but could you translate that.

It's working well and booting my menu.lst on the second HD without the boot option.
I must have missed it in the cut and paste.

---

### Post by ibuclaw on 2008-07-17
That's good too know.

As for your answer. As I stated, it's for interactive booting of kernels.

I can't quite remember the option at the moment, but you can drop into an interactive shell at the grub boot menu stage.
From there you boot up your own kernel, and use the command "boot" to tell grub that it is the end of the boot config and that you wish for it to run.

Regards
Iain

---

### Post by philinux on 2008-07-17
Ok, thanks, so I'm not running an interactive command line on sdb so the "boot" option is redundant for my system.

For info I've got Hardy on HD0 and Intrepid on HD1.

So now with grub on HD1 as well I've got tidy menu.lst's on both drives.

---

### Post by ibuclaw on 2008-07-17
Ah, yes... I've got Intrepid setup on my testing machine :D

Nvidia Graphics...Working! (Just needed to comment out the **Section Files** section in my xorg.conf file).
Compiz...Working! 3D Windows and Deformed Cube... :D

The only hitch I've had so far is that after the first upgrade, the bootsplash breaks.

Well... that and the "Bailey's Cream" on "80% Dark Chocolate" look in OpenOffice... ;)

Have fun!

Regards
Iain

---

### Post by philinux on 2008-07-17
I'm not sure I like the new theme. I'm not customising anything just so I test as is.

Having fun...

---

