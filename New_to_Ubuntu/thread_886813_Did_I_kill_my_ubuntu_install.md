---
title: "Did I kill my ubuntu install???"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by smergs on 2008-08-11
So I've been playing around with ubuntu 8.04 for the last week or so.  I've been really enjoying the OS and had started to get brave enough to try different things out.  I ended up installing Wine this morning and then installed steam.  After the steam install was complete I installed the original half-life.   To my surprise it was working fine when I first started playing.  I was riding in on the train and jumping around and after about 5 minutes or so it just froze.  I couldn't find a way to get out of it so I ended up pressing the reset button on the front of my computer.  When I started it up I started to see the following message scrolling over and over.

descriptor -top/console_setup: /scripts/init-top/console_setup: 1: 11: Bad fil

I may not have it exactly right but it was something really close to that.  So am I going to have to do a complete reinstall or is there a way to repair this? 

:confused:

---

### Post by fahadsadah on 2008-08-11
See if booting into recovery mode helps.

---

### Post by smergs on 2008-08-11
> **fahadsadah said:**
> See if booting into recovery mode helps.

I'm a complete n00b here.  Can you explain how I can do that please?  Thanks!

---

### Post by fahadsadah on 2008-08-11
Reboot/turn on your computer. As it boots, there is something that says GRUB Stage 1.5 or similar. Repeatedly press the escape key, until a menu comes up. Select the second option.

---

### Post by smergs on 2008-08-11
> **fahadsadah said:**
> Reboot/turn on your computer. As it boots, there is something that says GRUB Stage 1.5 or similar. Repeatedly press the escape key, until a menu comes up. Select the second option.

Ok.  I did that.  Now at the bottom of the screen I see the following:
Loading, please wait...
/scripts/init-top/all_generic_ide: /scripts/init-                top/all_generic_ide: 18: -13107
4: Bad file descriptor

Any ideas?  Looks like it is just frozen at this point.

---

### Post by smergs on 2008-08-11
I let it sit at that recovery screen for a while and then just restarted the computer.  When it restarted it came right back up!  Thanks!

---

### Post by Crafty Kisses on 2008-08-11
> Ok. I did that. Now at the bottom of the screen I see the following:
Loading, please wait...
/scripts/init-top/all_generic_ide: /scripts/init- top/all_generic_ide: 18: -13107
4: Bad file descriptor

Sounds like your filesystem is corrupt, when in recovery mode run this:
```
fsck
```

---

