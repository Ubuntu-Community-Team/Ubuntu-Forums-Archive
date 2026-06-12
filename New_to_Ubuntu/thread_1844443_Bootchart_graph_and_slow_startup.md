---
title: "Bootchart graph and slow startup"
date: 2011-09-15
forum: New to Ubuntu
---

### Post by mutt|ey on 2011-09-15
Hi all,

 i have an Intel(R) Core(TM) i7 CPU Q 740  @ 1.73GHz with 8 gb ram, at the end a good pc i think...

but the startup is not very speedy, this is my bootchart graph:
[[IMG]http://img710.imageshack.us/img710/5643/meanmachinenatty2011091.png[/IMG]](http://imageshack.us/photo/my-images/710/meanmachinenatty2011091.png/)

I see that my hd is always busy, but more than 1 mnutes for this machine i think is too much.

Anyone can help me to understand where and how change my config.

thanks!

---

### Post by texaswriter on 2011-09-15
i bootup with as few processes on startup as possible (as close to zero as possible). this goes for linux or windows. i'll load extras after login. 

also check your bios settings for tests on boot, sometimes these are performed silently.

---

### Post by mutt|ey on 2011-09-15
first of all, thanks for answer!

how can start services/daemons/process after login? with runlevel? after 4 or 5 runlevel?...or kde autostart folder?

there isn't bios test at start, but also if present, i don't think bootchart count also boot time...i think it's only start count when i select os on grub, isn't it?

---

### Post by texaswriter on 2011-09-18
> **mutt|ey said:**
> first of all, thanks for answer!

how can start services/daemons/process after login? with runlevel? after 4 or 5 runlevel?...or kde autostart folder?

there isn't bios test at start, but also if present, i don't think bootchart count also boot time...i think it's only start count when i select os on grub, isn't it?

Somebody else can answer your question about runlevels... 

I make a script and run it after login, as in manually. That's enough for me, but hopefully somebody else can provide you more information if that's where you want to go.

---

