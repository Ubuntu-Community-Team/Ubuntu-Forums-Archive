---
title: "System hangs after ~20 minutes idle"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by sirwhiteout on 2008-09-12
Hi,

I have been running Ubuntu 8.04 on a Toshiba Satellite A210 PSAFGE laptop, and it has worked well until a few days ago, when it started hanging a few minutes after the screensaver kicked in. It doesn't happen immediately, but only after about 20 minutes. The system stops responding entirely and only the Alt+SysRq+REISUB combination works on it.

Any help would be appreciated to solve this, as I don't even know where to start looking for the problem.

---

### Post by unutbu on 2008-09-12
Does Ctrl-Alt-Backspace return you to the login screen? This is obviously not a solution, but it is better than Alt-SysRq-REISUB.

I wonder if your problem is the same as this:
[http://ubuntuforums.org/showthread.php?t=916386](http://ubuntuforums.org/showthread.php?t=916386)
If it is, at least you will know it is related to the 'suspend' operation.

---

### Post by sirwhiteout on 2008-09-13
> **unutbu said:**
> Does Ctrl-Alt-Backspace return you to the login screen? This is obviously not a solution, but it is better than Alt-SysRq-REISUB.

Unfortunately, no. I've tried every keyboard shortcut I heard of (Ctrl+Alt+Backspace, Ctrl+Alt+F1, Ctrl+Alt+Del, etc.), but the SysRq is the only one apart from hard-switching it off that works.

> **unutbu said:**
> I wonder if your problem is the same as this:
[http://ubuntuforums.org/showthread.php?t=916386](http://ubuntuforums.org/showthread.php?t=916386)
If it is, at least you will know it is related to the 'suspend' operation.

I don't think so, because its suspend function is disabled. Entering the screen saver, or being idle long enough that the screen blanks is enough for the system to hang.

---

### Post by billgoldberg on 2008-09-13
I don't really know what the problem is, but why don't you just disable the screensaver function?

---

### Post by unutbu on 2008-09-13
This might amount to the same thing as what billgoldberg just suggested, but in case it is different and case his suggestion doesn't work, perhaps try this:
```

xset -dpms
```
This will turn off DPMS (Display Power Management Signaling).

Run it in a terminal, and then let your laptop idle for 20 minutes.

---

### Post by sirwhiteout on 2008-09-14
> **billgoldberg said:**
> I don't really know what the problem is, but why don't you just disable the screensaver function?

I tried disabling it and left the computer running overnight, and it seems to have worked. Thanks!

> **unutbu said:**
> This might amount to the same thing as what billgoldberg just suggested, but in case it is different and case his suggestion doesn't work, perhaps try this:
```

xset -dpms
```
This will turn off DPMS (Display Power Management Signaling).

That didn't work. The computer still froze. :(

But The strange thing is that this problem has just appeared a few days ago, and I've been running Ubuntu for almost two months without anything like this ever happening before.

The one different thing I've done lately was enabling backport updates. Could it be that this caused the problem?

---

### Post by unutbu on 2008-09-14
I'm glad you found a way to avoid the problem. 
Perhaps this was caused by the installation of a new or upgrade package.

Look in /var/log/dpkg.log. This will tell you what packages have been installed on what dates. Look in /var/log/dpkg.# or /var/log/dpkg.#.gz if your logs have rotated and you need to look back further.

Perhaps look for any package having to do with the screensaver.

Knowing what package is causing the problem would be a good start on finding a fix.

---

### Post by R_T_H on 2008-09-14
I had a similar problem with 7.04 Xubuntu. After the screensaver kicked in, if I tried to get it going again it would just show a black screen with the white cursor. I solved this by using "xscreensaver" as opposed to the default screensaver program.

---

