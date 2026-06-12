---
title: "Need to recreate grub menu.lst"
date: 2008-04-20
forum: Other OS Talk
---

### Post by talikarng on 2008-04-20
I can currently dual boot windows xp and kubuntu through the grub menu. I recently installed freebsd onto  a spare partition (this means that i would triple boot) but the freebsd loader didn't let me go into kubuntu.

I reloaded grub from the livecd and pointed it back to my kubuntu partition but my question is: How can I get grub to add my freebsd partition to menu.lst without having to reinstall kubuntu?

---

### Post by banewman on 2008-04-20
Does typing
sudo update-grub
in a konsole give you any luck?

---

### Post by mick8985 on 2008-04-20
The simplest way is to do something like

```
 title        FreeBSD
 root          (hd0,1)
 makeactive
 chainloader   +1
```

Where (hd0,1) refers to the partition you have BSD on, so amend to wherever you installed it

---

### Post by talikarng on 2008-04-22
Thankyou to both of you;

I had to put in the code above without the makeactive line and it worked. What does the makeactive line do anyway?

---

### Post by Ptero-4 on 2008-04-22
It makes that partition the active one, this is mostly required for M$ Windoze.

---

