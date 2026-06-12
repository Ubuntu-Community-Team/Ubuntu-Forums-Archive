---
title: "Default a brightness level on Ubuntu brightness-indicator applet"
date: 2014-02-10
forum: New to Ubuntu
---

### Post by thomsebastin on 2014-02-10
Hey guys:), hope u all doing good.I need ur help with a brightness indicator app.My problem is that I have this brightness indicator app that I use too often to control the brightness of my laptop screen.Every time I shutdown my computer n restart it,the first thing I do is to control the brightness level from 7 to 2(there are upto 7 from 0).I really would loved it if there was a way to set the brightness to a different level,say 2..n the same level to be there even on the next restart.Any method is appreciated.Alternative apps which r capable of doing the same are also welcomed.I can provide you with whatever details that u need so as to solve this problem.I wish I didn't confuse you.Sorry if I'm not clear.

---

### Post by sandyd on 2014-02-10
Does running something like
```

echo 2 > /sys/class/backlight/acpi_video0/brightness
```
change the brightness of your screen?

If so, you can just make that command to run on boot

---

### Post by thomsebastin on 2014-02-11
> **sandyd said:**
> Does running something like
```

echo 2 > /sys/class/backlight/acpi_video0/brightness
```
change the brightness of your screen?

If so, you can just make that command to run on boot

Thank you sandyd.Yes this solved my problem.Marking this thread **solved** right away.

---

### Post by andreas20 on 2014-06-02
When i write the command in terminal it says "Permission denied". I have tried with sudo.
Any idea how to fix this?

---

### Post by owenll on 2014-06-02
Detailed guide in this post: [http://ubuntuforums.org/showthread.php?t=2217524&p=12991034#post12991034](http://ubuntuforums.org/showthread.php?t=2217524&p=12991034#post12991034)

---

