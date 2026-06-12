---
title: "Error 15 File Not Found during installation"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by coldfire204 on 2008-06-20
Hello,  I just tried to install Ubuntu 8.04 using the 'Install Inside Windows' option on the CD, and also by trying the full installation install as well.  With both methods of installing, I get to the screen where you can pick which OS you want to load (for me, it's either XP or Ubuntu.)  If I pick Ubuntu I get an error message saying something to the effect that menu.lst is missing.  Should I just try reburning this onto another disc or something?  I  usually don't have any problems like this, I always burn stuff at the slowest possible setting.  My system and DVD burner aren't top of the line, but they don't suck either.  

If it matters, I'm using a DVD writer to burn, but using CD-R to put the program on, instead of a blank DVD.

Any help is appreciated, thanks.

---

### Post by Prospero2006 on 2008-06-20
I had this problem as well when I tried to do a dual-boot install XP/Ubuntu.
Here's what you should do:

Boot the live CD and access the filesystem on which the operating system is installed. 

Use a text editor to access /boot/grub/menu.list

Within that file there are parameters defined for each O/S. The incorrect parameter is most likely listed like this hd: (1,0) or something similar.
Start by changing the numbers in parentheses. Start with (0,0) and move up.
Eventually, I'd be willing to bet grub will pick up the disk correctly and boot.

?

---

### Post by coldfire204 on 2008-06-20
I tried opening the menu.lst file from a command prompt, but I get an error 27: Unrecognized command.  I can't even cd to switch out of the default directly GRUB>.  None of the usual commands that work in a UNIX shell work.. so I tried finding the file on the installation on my E drive in Windows.  I found it, but it's just a bunch of gibberish characters, so no help there.  Is vi still the standard UNIX text editor, or is there something else I should be trying to open this thing with?

---

### Post by Prospero2006 on 2008-06-20
Boot a live cd like knoppix maybe, or the Ubuntu installation disc.
You can use one of the text editors from gnome. Or at the command line, I find pico is easy for quick fixes if you aren't familiar with vi or emacs.

---

### Post by coldfire204 on 2008-06-20
lol, well, apparently all I had to do was move the installation from the E: drive to the C: drive, now it works just fine.  Thanks for your help though!

---

