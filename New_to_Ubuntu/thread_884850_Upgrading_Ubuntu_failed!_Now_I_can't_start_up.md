---
title: "Upgrading Ubuntu failed! Now I can't start up"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by Bakhman on 2008-08-09
I tried upgrading to 8.04 the other day (finally) and it froze while upgrading.
So I tried to restart the computer, and it freezes on the orange screen. I am able to move my mouse and all but is there any way to revert back to the old version of Ubuntu?

I tried going to the setup menu (pressing F12, I have a Dell) and it lets me pick between v7 of Ubuntu as well as "Recovery mode" of v7. Neither worked.. can someone with Dell knowledge explain step-by-step what to do here? I miss my laptop...

---

### Post by Victormd on 2008-08-09
Unfortunately downgrading from Hardy to Gutsy isn't possible, you'd have to do a fresh install of Gutsy...

How did you go about upgrading? Did you do a fresh install or using the upgrade manager? If you used the upgrade manager, I would suggest doing a fresh install of Hardy instead. When I tried upgrading through the upgrade manager I ran into a series of problems and thought to myself "oh crap, why did I do this"... then, after a fresh install, I was impressed at how Hardy was able to detect everything on my laptop and is working great!

---

### Post by coolbrook on 2008-08-09
Did your upgrade freeze while generating locales?

If so then consider [this thread](http://ubuntuforums.org/showthread.php?t=865679)

---

### Post by Bakhman on 2008-08-09
Thanks for the link cool, but I did try going to the GRUB menu and picking an earlier version and it still did not work.. the rest of the thread I really cannot understand ..:oops:

> **Victormd said:**
> Unfortunately downgrading from Hardy to Gutsy isn't possible, you'd have to do a fresh install of Gutsy...

How did you go about upgrading? Did you do a fresh install or using the upgrade manager? If you used the upgrade manager, I would suggest doing a fresh install of Hardy instead. When I tried upgrading through the upgrade manager I ran into a series of problems and thought to myself "oh crap, why did I do this"... then, after a fresh install, I was impressed at how Hardy was able to detect everything on my laptop and is working great!

I did use the upgrade manager.
So how do I do a "fresh install" of Hardy? Do I burn it on a disc and it will still be detected even though I don't have an OS? Also will I have to get rid of Gutsy once I have Hardy (I wouldn't want both..) Thank you so much!!

---

### Post by Victormd on 2008-08-10
To do a fresh install, just download and burn the ISO. You'll need to set the BIOS to boot from the CD and then wen you boot, it will give you a few options (i.e., try Hardy, install...). If you install on the same partition, it will format and install Hardy, wiping out Gutsy. With that in mind, use the Live CD to access your files and backup all your data before installing.

---

