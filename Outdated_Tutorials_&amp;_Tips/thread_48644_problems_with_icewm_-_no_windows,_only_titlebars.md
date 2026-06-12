---
title: "problems with icewm - no windows, only titlebars"
date: 2005-07-13
forum: Outdated Tutorials &amp; Tips
---

### Post by subatomic on 2005-07-13
I have a pentium 266 with 32 meg of ram...   as such I wanted a very small lean install using icewm and xdm.   I started with the Ubuntu (hoary) installer (with "**server**" option at boot: ).  This is probably a known bug (i hope), but the installer fails when detecting network devices and then crashes.   I was able to get around this and finally install after I created a swap partition, then rerun the install, then during the install process switch to another virtual terminal to run a command to enable the swap partition (mkswap and swapon).  from there, everything baseline installed just fine.

then... the **problems** began!   I wanted to install a window manager (icewm to be specific).  so I did this:

```
# apt-get update
# apt-get install icewm
# apt-get install xserver-xfree86
# apt-get install x-window-system-core
# apt-get install xdm
# apt-get install numlockx
# apt-get install xterm
```

after rebooting, xdm starts and I log in, icewm runs and looks good.

but it's _not good_!  when I run xterm (or any application, including "logout"!), the titlebar appears but the window portion is missing!.  It's just a decapitated head (erm... titlebar) floating in space.   If I right click on the titlebar and choose [FONT=Courier New]fullscreen[/FONT],  THEN I see the window (but it's ferkin' fullscreen, not cool, right?).   Playing with the [FONT=Courier New]shade[/FONT] and [FONT=Courier New]resize[/FONT] menu options do not make the window appear.   ](*,)     Changing to other themes doesn't help, in fact some themes also make titlebar disappear (so that no part of the window appears on the desktop, except for in the task bar).

**Does anyone understand what is going on?   **  running [FONT=Courier New]top[/FONT], I do see [FONT=Courier New]Xorg[/FONT] in the process list running as root.


thanks for any help.

---

### Post by subatomic on 2005-07-13
I moved the topic to "Ubuntu Hoary Hedgehog 5.04  > Hoary 5.04 Application Support  > Installation Help":  
[http://www.ubuntuforums.org/showthread.php?p=253985#post253985](http://www.ubuntuforums.org/showthread.php?p=253985#post253985)

It seemed more appropriate.   Maybe someone could delete this thread for me?


If you respond, do it in the other thread, thanks...

---

