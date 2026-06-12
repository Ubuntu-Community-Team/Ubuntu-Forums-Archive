---
title: "[SOLVED] How do I get my splash back"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by Michaelg14 on 2008-11-28
My bootup splash screen is not working.  I get the Ubuntu screen for a few seconds then it disappears and I get "files needed to boot" and a bunch of text.  As far as I can tell there is no error message or any reason for the splash screen to go away.  How do I get it back?

---

### Post by __Ryan__ on 2008-11-28
First things first.  If you look in: 

/boot/grub/menu.lst

At the end of the "kernel" line does it have the "splash" option specified. If not you should add it.  Be careful not to touch anything else in this file as it may affect your ability to boot Ubuntu correctly.

If it has this already you should print the output of the "dmesg" command.

---

### Post by Michaelg14 on 2008-11-28
I do have quiet splash on the end of the kernal line.  I noticed that there is a section in menu.lst that addresses this also.

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

BUT:

The section on how many kernals to show is set to 2 but three (so far) show up when grub runs. So, things are not working as advertised.

The output of dmesg scrolled off the top of my terminal, are you looking for something in particular?

---

### Post by Keen101 on 2008-11-29
> I do have quiet splash on the end of the kernal line.

while i don't know how to exactly fix your problem, try to delete the word "quiet" at the end of your kernel line. Technically it should should display the usplash screen, but will also display small colored text underneath.

---

### Post by Michaelg14 on 2008-11-29
Good thought... didn't work.  I got even more text and no splash screen.  When the original screen disappeared the next thing on the screen said:

reading files needed to boot.

That phrase appeared after several pages of text with quiet removed from grub.  Very interesting...


Thanks anyway.

---

### Post by PocketDog on 2008-11-29
Have you moved or changed your swap partition, or re-sized it? Your problem is what happens when the swap UUID doesn't match

---

### Post by mbsullivan on 2008-11-29
Hi Michaelg14,

Have you seen [this article]("http://ggts.net/2008/05/13/reading-files-needed-to-boot/")? It seems to describe your problem, along with a possible fix.

Mike

---

### Post by Michaelg14 on 2008-11-29
That seems to be my problem, I don't use a swap partition I have a swap file.  It boots up and works so I guess I won't worry about it.

---

