---
title: "FireFox Hangs, 99% CPU"
date: 2012-03-16
forum: New to Ubuntu
---

### Post by Glkanter on 2012-03-16
This is what seems to be happening just in the last couple of days:[INDENT]I'll leave my PC
Come back a couple hours later
All the Firefox instances are unresponsive
System Monitor shows 99% cpu usage for Firefox

[/INDENT]I'll kill FireFox, and things will be OK, I guess.

I've sorta switched to Chromium, and it does not have this problem.

I use Ubuntu 11.04.

Is it me, or has anyone else had this problem?

---

### Post by NikTh on 2012-03-16
Hi , 
Maybe some add-ons are responsible for this behavior . Try to start Firefox without add-ons.

---

### Post by winh8r on 2012-03-16
Could be connected to addons or extensions.

try starting firefox in safe mode from the terminal


```
firefox -safe-mode
```

to see if the problem still shows.

You can also check by disabling add-ons and extensions one by one.

---

### Post by Glkanter on 2012-03-17
Thank you both.

I disabled a couple of add-ons and the problem seems resolved.

Thank you, as always!!

---

