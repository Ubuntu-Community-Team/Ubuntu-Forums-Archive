---
title: "Show dualboot only when certain button is pressed during startup"
date: 2012-08-23
forum: New to Ubuntu
---

### Post by Uyt on 2012-08-23
Hello
I'm new to Linux but I want to install a dualboot of windows 7 (already installed) and Ubuntu. I'm not the only one who use this computer. Thats why I want the dualbootscreen only show up when certain button(s) are pressed when the computer is turned on. Else Windows schould start immediately so they won't see the dualbootscreen and they won't get in trouble. Is this possible?

Thank you already!!!

Ps: English is not my foreign language so please don't be evil to me because of my faults. ;)

---

### Post by klytu on 2012-08-23
Assuming you are using Grub2 as your bootloader (I think this is the default when you install Ubuntu), you can make Windows the default selection then password protect other entries (which you can also hide). Other people won't be able to use the password protected choices unless they know the correct password. Take a look at this:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

especially items number 4 and 10

By the way your English is fine. I'm a typical lazy American so I only know one language; it's great that you know more than one. :-)

---

### Post by jemofthewest on 2012-08-23
You can also set the Windows partition to default and set GRUB_HIDDEN_TIMEOUT to true so that way the grub menu doesn't even show unless you push a button.  Check out [this article]("https://help.ubuntu.com/community/Grub2#Hidden") for more details and options.

EDIT: That's in the article posted above as well... sorry!

---

### Post by Uyt on 2012-08-23
Thanx for your quick replies. I'm gonna try this as fast as possible.:)

---

