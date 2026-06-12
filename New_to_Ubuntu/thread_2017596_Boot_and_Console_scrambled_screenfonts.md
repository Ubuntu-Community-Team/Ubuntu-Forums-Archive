---
title: "Boot and Console scrambled screen/fonts"
date: 2012-07-05
forum: New to Ubuntu
---

### Post by h4sy0u on 2012-07-05
Hi i am new in Ubuntu. Currently i am using 12.04 64bit ver. with nvidia Gerforce 6 and 295.49 drivers.
My problem is i have bad screen fonts while booting/console it is unreadable, and in console (ctrl+alt+f1) i cant see what i am typing because of this.

For example there is my boot/console screens.
[IMG]http://img839.imageshack.us/img839/1144/20120705213702.jpg[/IMG]

[IMG]http://img193.imageshack.us/img193/530/20120705213718.jpg[/IMG]

Have you some ideas how to fix this ?

---

### Post by h4sy0u on 2012-07-07
bump

---

### Post by Earendil1982 on 2012-08-03
I'm affected by this as well for months if not years.
Nobody got any idea?

I'm also using a nvidia but can't tell you the details, as my system won't boot at the moment and I can't tell why&#8230; :/


Edit:
Well, this is what helped me:

- edit the file /etc/default/grub (as root)
- search the lines 
GRUB_GFXMODE=...
GRUB_GFXPAYLOAD=...
- change them to a reasonable resolution for your system, in my case
GRUB_GFXMODE=1024x768x24
GRUB_GFXPAYLOAD=1024x768x24
- save the file
- run update-grub in the terminal (as root)
- reboot
-> and you're done

Hope it helps&#8230;

---

### Post by fbicknel on 2013-04-08
In my case, the console was blank, but when you type you got a glimpse of what was going on for the line you're on... then it would disappear immediately.

Your fix worked.  There was no GFXPAYLOAD parameter, so I tried it without.  Didn't work unless I added both.

Now when I return to the X screen, Compiz crashes... but that's another problem.  *sigh*

Lenovo ThinkPad W510
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"

---

