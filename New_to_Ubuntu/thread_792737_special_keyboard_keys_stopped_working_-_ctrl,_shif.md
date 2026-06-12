---
title: "special keyboard keys stopped working - ctrl, shift, alt"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by Fatman_UK on 2008-05-13
i have the exact same issue as in this thread. [please forgive lack of caps in this post, but i'm unable to type them right now. also i'm not sure the prefix is right. i installed ubuntu but it seems to have changed to kubuntu when i installed kde as an alt to gnome.]

[http://ubuntuforums.org/showthread.php?t=740216](http://ubuntuforums.org/showthread.php?t=740216)

strangely, i also am running vmware [server]. i am not keen to reinstall it as it is an absolute nightmare to get working. this will be a last resort.

the first i knew of this bug was when firefox 3 beta 5 crashed followed rapidly by the gimp, after a few hours of working fine.

i upgraded this system to hardy recently, and i'm not using any special keyboard drivers.

i did have some problems with the gtk libraries recently, which i solved by reinstalling them. i wonder if this could be gtk related - firefox and gimp are affected, but konsole apparently not.

is this a vmware problem, or xkbd, or what [question mark]

thanks.

---

### Post by Fatman_UK on 2008-05-15
Well I found a workaround but it's not exactly helpful - don't start VMware Server. When I'm forced to start VMware Server, the keyboard goes nuts again. Oddly, the keyboard works fine in the guest OS (WinXP).

I have to reboot to fix it, which as everyone knows is anathema to Linux users, so any ideas would be appreciated.

Thanks.

---

### Post by waynema on 2008-05-18
the post below may be helpful, good luck
  [http://ubuntuforums.org/showthread.php?p=4990785#post4990785](http://ubuntuforums.org/showthread.php?p=4990785#post4990785)

---

### Post by Fatman_UK on 2008-06-04
```
ajr@ajr-desktop:~$ xmodmap
xmodmap:  up to 1 keys per modifier, (keycodes in parentheses):

shift
lock
control
mod1
mod2
mod3
mod4
mod5

ajr@ajr-desktop:~$ setxkbmap
ajr@ajr-desktop:~$ xmodmap
xmodmap:  up to 2 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x6d)
mod1        Alt_L (0x40),  Meta_L (0x9c)
mod2        Num_Lock (0x4d)
mod3
mod4        Super_L (0x7f),  Hyper_L (0x80)
mod5        Mode_switch (0x5d),  ISO_Level3_Shift (0x7c)
```

Hurrah! Thanks waynema.

Sorry it took so long to reply, it took two weeks to work up the courage to use VMWare Server again. :) What a strange bug...

---

