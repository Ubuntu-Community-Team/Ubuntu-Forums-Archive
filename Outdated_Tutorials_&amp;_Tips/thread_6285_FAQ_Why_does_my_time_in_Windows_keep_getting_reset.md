---
title: "FAQ: Why does my time in Windows keep getting reset to UTC?"
date: 2004-11-27
forum: Outdated Tutorials &amp; Tips
---

### Post by Rancoras on 2004-11-27
Ubuntu assumes by default that the system clock is set to UTC.  To change this behavior:

```
sudo gedit /etc/default/rcS
```

Find the line     UTC=yes
Change it to     UTC=no

Save the file.

The next time you reboot to Windows, your time will be correct.  (Assuming that the time in Ubuntu was correct when you edited the file)

---

### Post by clparker on 2005-06-20
Thanks boss, that did the trick!

---

### Post by Neo Anderson on 2005-07-09
ohh..thanks alot... :-)

---

### Post by sciurus on 2005-12-13
Even with this properly set, I've seen a Kubuntu 5.10 / Windows XP dual-boot system where Windows time was correct but linux was stuck on UTC. The problem was that /etc/timezone was missing; the solution was to make it a symlink to the proper timezone in /usr/share/zoneinfo.

---

### Post by Keith_Dreamz on 2007-03-18
Hey Guys but where do i find UTC?????????????????:(

---

