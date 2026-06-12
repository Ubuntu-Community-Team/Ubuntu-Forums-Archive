---
title: "[SOLVED] I broke my ubuntu :("
date: 2008-07-14
forum: New to Ubuntu
---

### Post by cobaltinfinity on 2008-07-14
I've been using Gutsy for a while and I just decided to upgrade to Hardy Heron. It had all loaded up fine but then it gave me the option of installing a third party graphics driver for my Nvidia graphics card.

I installed it and rebooted, but the next time it tried to load the log-in screen, my monitor blacked out and put "Out of Range!" on screen. What's going on??? Ubuntu is still technically working because I called up the terminal blind and keyed in the sudo restart command. So I can still do stuff from here providing I don't make typos! 

I didn't even need to install the driver really, it was working fine. Is there anyway I can reverse the install? I tried using recovery mode but it still wouldn't give me a picture.:confused:

Now I'm back on XP typing this. boooo! 

Any suggestions would be greatly appreciated!

---

### Post by scragar on 2008-07-14
```
sudo dpkg-reconfigure xserver-xorg
```
that should reset the graphics card(just answer the questions, if you don't know the defaults are properly best, or you can ask here).

---

### Post by BigT0 on 2008-07-14
try this out. something i saw around the forum..
get yourself a pen and paper and write it down cause its all terminal without gnome 

[http://ubuntuforums.org/showthread.php?t=399630](http://ubuntuforums.org/showthread.php?t=399630)

---

### Post by louieb on 2008-07-14
xorg in hardy is different.  It tries to auto detect your monitor. 
 To get x back boot to** recovery mode** select the xfix option. then the resume normal boot option.  That should get x back. 

To set your max screen resolution from a terminal window 
```

gksudo displayconfig-gtk
```

---

### Post by cobaltinfinity on 2008-07-15
> **louieb said:**
> xorg in hardy is different.  It tries to auto detect your monitor. 
 To get x back boot to** recovery mode** select the xfix option. then the resume normal boot option.  That should get x back. 

To set your max screen resolution from a terminal window 
```

gksudo displayconfig-gtk
```

Thanks! This worked! :D

Thanks to everyone else who suggested stuff as well. I can't believe how quick the responses are here!

---

### Post by Troll_the_Great on 2008-07-15
Glad we could help.Please mark your thread as solved if you don't need further assistance.This way other people can benefit, and the forum members won't waste their time looking at threads that are already solved.
Cheers!

---

### Post by barbedsaber on 2008-07-15
It seems that the OP is gone, but can I also ask, (for when they get back) that they use a more descriptive title.

---

