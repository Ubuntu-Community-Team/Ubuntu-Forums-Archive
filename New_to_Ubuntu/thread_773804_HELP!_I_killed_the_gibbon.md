---
title: "HELP! I killed the gibbon"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by scientist1971 on 2008-04-29
was using ubuntu and decided to change the graphics driver (thought it would then enable me to run a game I have been having problems with)
REALLY bad idea
after a restart nothing - ubuntu would not load up at all
after a memory check I now get the ubuntu logo then the terminal asking me to log in 
after I have done that nothing...
just get the terminal message asking for input i.e.
name@name-laptop:~$_

I have absolutely no idea what to type here to get ubuntu started again

---

### Post by Michael.Godawski on 2008-04-29
how did you install the new driver? What is your graphic card?

You can try to reconfigure the xserver with
```

sudo dpkg-reconfigure xserver-xorg -phigh
```

---

### Post by scientist1971 on 2008-04-29
through the sound settings in the admin menu
cannot tell you what the card is I am using xp in japanese and the owner of the computer does not know how to find this info in xp and my japanese is too limited

---

### Post by Joeb454 on 2008-04-29
What happens if you log in then type ```
startx
```

---

### Post by scientist1971 on 2008-04-29
startx will try that

when I tried:

root@name-laptop:~# sudo dpkg-reconfigure xserver-xorg - phigh

I got:

xserver-xorg postinst warning: overwriting possibly - customised configuration file:back up in/etc/X11/xorg.conf.20080429183553

then:

name@name-laptop:~$

but did not know what to do next....

---

### Post by scientist1971 on 2008-04-29
I restarted to try startx but ubuntu started normally anyway
michael thanks a lot for your help
and cheers for your suggestion too joeb
however all the symbols on my keyboard are mixed up!
dont suppose you know anything about that too guys?

---

### Post by billgoldberg on 2008-04-29
> **scientist1971 said:**
> I restarted to try startx but ubuntu started normally anyway
michael thanks a lot for your help
and cheers for your suggestion too joeb
however all the symbols on my keyboard are mixed up!
dont suppose you know anything about that too guys?

Try the keyboard language settings in:

system -> preference -> keyboard

---

