---
title: "Boot up verbose/quiet mode"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by brandoncolorado on 2008-11-30
When I boot Ubuntu 8.10, I see a lot of lines of text, then the splash screen, then probably 15-20 more lines of status/commands.  I assume that this means that I am in 'verbose' mode?  Or is this as 'quiet' as the 'quiet mode' gets?  I searched google and these forums, and I think I am using the wrong terminology.  I found this in my /etc/boot/grub/menu.lst file:

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

If I uncomment that last line, will I be in quiet mode?  Does it matter that I am using WUBI?

---

### Post by sdennie on 2008-11-30
Uncommenting that line will not fix the problem (and will probably cause problems).  Without seeing the output you are seeing, I can't say for certain why you are seeing lots of text during the boot process but, if you are seeing the splash screen, that probably is as quiet as you are going to get.

---

### Post by Barriehie on 2008-11-30
I found a reference to verbose=yes/no in /etc/default/rcS  See man rcS for details.

Barrie

---

