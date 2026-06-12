---
title: "[SOLVED] Grub error"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by rfbeck on 2008-11-29
I have a dual boot system. Ubuntu/ WinXP. Ubuntu is on my smaller 250 MB drive and XP is on my 1TB drive. Only recently(it's worked fine until now) when I boot my computer I get a freeze on boot witn the message "GRUB ERROR".

When I boot several more times my computer simply will boot into WinXP.

I would like to fix this by reinstalling the GRUB menu. How do I do this? 

By the way which drive is my GRUB menu installed on anyway? Thanks.
______
Robert

---

### Post by falcon61102 on 2008-11-29
What specifically is the GRUB Error that pops up?  It should have a number associated with it, like GRUB Error 17.

You can reinstall the GRUB by using a LIVE CD.  Boot your computer from the live CD and then open up a terminal by going to Applications>Accessories>Terminal

Then type the following:
```
sudo grub
```

This will load the GRUB menu, next you want to find where the GRUB is installed:
```
find /boot/grub/stage1
```

That should give you the output of something like (hd0,1) which you will use in the following steps:
```
root (hd0,1)
setup (hd0)
```

Notice in the setup step, you only use the first number of the (hd0,1) output.

That should reinstall your GRUB.

---

### Post by Duck2006 on 2008-11-29
Some info on grub.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by rfbeck on 2008-11-29
Usually it just stops at "GRUB ERROR" but sometimes I get error 16.
______
Robert

---

### Post by meierfra. on 2008-11-29
> Usually it just stops at "GRUB ERROR" but sometimes I get error 16.

Error 16 is often caused by loose or damaged cables.  The inconsistent behavior also indicates a hardware problem. So check out your hard drive cables.

For more information:

[http://users.bigpond.net.au/hermanzone/p15.htm#16]("http://users.bigpond.net.au/hermanzone/p15.htm#16")

---

### Post by It_Was_Luck on 2008-11-29
Might be helpful... but when your working with dual booting you really have to mind the MBR on each HDD, and the [SuperGrub Live CD]("http://www.supergrubdisk.org/") might come in handy later...

---

### Post by rfbeck on 2008-11-30
Okay problem solved, first I did what meierfra said and checked for loose cables. Then I did what falcon61102 said and reinstalled the GRUB menu and now I have a properly working menu. Thanks guys.
______
Robert
ps how do I flag my problem as SOLVED?

---

