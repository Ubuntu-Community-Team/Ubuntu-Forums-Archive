---
title: "Can't get brightness to change on Toshiba Satellite L655"
date: 2013-04-28
forum: New to Ubuntu
---

### Post by TehPuddinz on 2013-04-28
I'm not sure if this is where i should put this but. 
My brother got me ubuntu today since i've been having problem's with Windows.
I really like it, but I can't change the screen brightness? 
I hate using my computer at night with the screen brightness up so much. 
I tried a few things that i've found, but some of the key strokes i used in the terminal wouldn't work.
I also tried simply changing the hot key's, hoping that would work but although it now 'tells' me i'm changing the brightness, nothing actually happens.
I tried going into the settings and although i scrolled the brightness up and down, once again. nothing happened. 
It would be really great if somebody could help me out. :3
Thank you to anybody who does!

---

### Post by pqwoerituytrueiwoq on 2013-04-28
[http://ubuntuforums.org/showthread.php?t=2139397&p=12621502&viewfull=1#post12621502](http://ubuntuforums.org/showthread.php?t=2139397&p=12621502&viewfull=1#post12621502)
look at the kernel boot parameters
the file to edit is [FONT=courier new]/etc/default/grub[/FONT]
after editing run [FONT=courier new]sudo update-grub[/FONT] and reboot

---

### Post by TehPuddinz on 2013-04-28
> **pqwoerituytrueiwoq said:**
> [http://ubuntuforums.org/showthread.php?t=2139397&p=12621502&viewfull=1#post12621502](http://ubuntuforums.org/showthread.php?t=2139397&p=12621502&viewfull=1#post12621502)
look at the kernel boot parameters
the file to edit is [FONT=courier new]/etc/default/grub[/FONT]
after editing run [FONT=courier new]sudo update-grub[/FONT] and reboot
when i put in /etc/default/grub it says 'permission denied' ? If I'm correct I'd do /etc/default/grub 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" GRUB_CMDLINE_LINUX=" 
all at once then hit enter?

---

### Post by pqwoerituytrueiwoq on 2013-04-28
you need to root access to edit that file, use [FONT=courier new]gksudo gedit /etc/default/grub[/FONT] gedit is just a example, some others are mousepad/leafpad/scite/geany

---

