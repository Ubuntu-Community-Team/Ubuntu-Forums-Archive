---
title: "But why's all the RAM gone?"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by chantzzzzz on 2008-09-30
Oh I know it was terrible, but hopefully it will get some people looking at this thread ;)

I've been using the 'top' command to quit processes that disappear on me (Lookin at you, VLC *glare* ), and I've noticed that 90% of my RAM is gone. Now what is happening here? I use Xubuntu (and Ubuntu in general) because it's light on the system. using 1800MB out of 2000MB worth of RAM is *NOT* light on the system. Someone please let me in on why this is happening, because in all honesty, Windows XP has NEVER used that much RAM. 

Two interesting facts: The computer does not seem to shut down as with windows where it comes into a fresh session. This might be the source of my problems, but I'm not sure. As well, Xubuntu is not using any of the SWAP partition, even though it acknowledges its existence. Odd.

Thanks in advance for any help!

Xubuntu 8.04 Hardy
Acer TravelMate 6592G
Intel Core2 Duo T7100 1.8GHz
800MHz FSB + 2GB RAM
ATI HD2400X

---

### Post by blithen on 2008-09-30
Woah... hmm...
In my opinion don't use TOP, use HTOP

```
sudo apt-get install htop
```
Post what program is using the most ram too please. (using htop, it sorts thing in according to it's memory usage.

---

### Post by philinux on 2008-09-30
Good explanation of linux memory usage.

[http://forums.gentoo.org/viewtopic.php?t=175419](http://forums.gentoo.org/viewtopic.php?t=175419)

---

### Post by sub2007 on 2008-09-30
That's nothing to worry about. Why have 2GB of RAM and not use it? Linux believes that any RAM not used is wasted RAM. So it will fill up all your available RAM by leaving programs in RAM that you have closed so that they will open faster. The kernel knows that it's not "real" RAM occupation and so it will displace any RAM when another program needs it.

Your swap partition should not be used, RAM is much faster to access than hard disk and so it will only swap when it absolutely has to.

---

### Post by TheLions on 2008-09-30
about RAM:
Linux doesn't leave free RAM to be unused, it puts cache in it...

about swap:
you can increase swappines if you wish, look here [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

EDIT:
a lot answers for one minute!!!

---

### Post by hyper_ch on 2008-09-30
unused ram == wasted ram

---

### Post by blithen on 2008-09-30
/delete post
Nevermind I'm a noob

---

### Post by TheLions on 2008-09-30
> **blithen said:**
> Then why on my computer that I never go over 500mb? when I have 2gb?

type top in terminal, gnome-system-manager don't show the cache!

---

### Post by blithen on 2008-09-30
> **TheLions said:**
> type top in terminal, gnome-system-manager don't show the cache!

I know. >.> I'm noob. I use htop though.

---

### Post by chantzzzzz on 2008-09-30
It would seem I have about 8 Firefox processes open (which I did close but they don't want to go away it seems) as well as about 20 or 30 of /usr/sbin/console-kit-daemon as well as two /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7 and a bunch of doubles like Thunar. How on earth do I get these to stop stealing my resources?

---

### Post by shifty_powers on 2008-09-30
i'm confused... is your computer actually unresponsive or slow with any programs or such like?

---

### Post by chantzzzzz on 2008-09-30
It doesn't seem to be. I guess it just seems weird to have almost a dozen firefox sessions open and doubles of almost everything

---

### Post by philinux on 2008-09-30
This is quite normal.

Try this command

pstree

---

