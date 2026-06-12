---
title: "Chicken and the Egg"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by BernardBoon on 2008-04-28
Hello,
I tried to install Ubuntu 7.10 32bit on my multiboot system and end up without a graphical display.
My display hardware is Nvidia 8600GT and on their web site I can download a driver suited for Linux OS's.
How can I install the driver without being able to boot into the new Ubuntu?
Thanks
BernardBoon

---

### Post by quirks on 2008-04-28
Can you switch to the textual interface at least (by hitting Ctrl+Alt+F1)? Or don't you see any output on your monitor at all?

---

### Post by encompass on 2008-04-28
Did the liveCD work?
If so, you should be able to get a graphical boot in your install.  Theoretically. :D

---

### Post by zvacet on 2008-04-28
Boot in recovery mode and type

```
dpkg-reconfigure -phigh xserver-xorg
```

select **vesa **driver and you should have basic graphic after restart.

---

### Post by encompass on 2008-04-28
I with thinking last night in bed about your issue, remember that nvidia's have issues like this if the bootup spash screen is going...
if you get a blank black screen this is worth a try...
When you computer turns on your going to see a count down that says something involved with grub.
If your doing dual boot this is where you select windows.  Or if you not... you can press esc here and select things like recovery mode.  But here we want to select the first menu item and press E to edit that like... then press down once... and press E again.
now move all the way to the end of that line.... delete the quite and splash
press enter and then B to boot
Any changes?  Can you get a graphical login screen now?  Hopefully, then we can make these changes permenent.

---

### Post by encompass on 2008-04-28
And the latest ubuntu version is also worth a try.  It works better with nvidia cards.
It is worth a try too.
But then... you haven't answered my questions yet... so I will wait.

---

