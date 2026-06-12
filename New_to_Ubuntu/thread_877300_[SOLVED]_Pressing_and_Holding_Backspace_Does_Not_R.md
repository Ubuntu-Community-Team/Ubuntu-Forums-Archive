---
title: "[SOLVED] Pressing and Holding Backspace Does Not Result in Rapid Deletion of Text"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by fredmv on 2008-08-01
Hi all, 

Not sure if this has been brought up before so if it has been, I apologize.  I couldn't conjure up what to use as a search string.  

All of a sudden, as the title implies, I can't simply hold down [Backspace] and have it delete all of the text prior to it.  Similarly, I can't hold [Space] and have it continually move the cursor forward.  The left/right arrow keys don't respond in the expected manner either.  

I'm running Xubuntu[xfce4.4]/hardy, and have utterly no clue what I might've done to cause this to happen.   Any input would be nice.

Thanks all.

---

### Post by mali2297 on 2008-08-01
Have you tried adjusting the keyboard preferences?

To reach them directly, open the run dialog (Alt+F2) and type
```

xfce-setting-show keyboard

```
(You can also go through the menus.)

---

### Post by fredmv on 2008-08-01
Thanks for the reply.

That's the thing:  I never edited the keyboard prefs to begin with.   I did however look into it, and everything seemed normal.     Tried editing some things but to no avail.

---

### Post by mali2297 on 2008-08-01
Try removing .gconf (hidden file in your home directory) and restart.

---

### Post by fredmv on 2008-08-02
> **mali2297 said:**
> Try removing .gconf (hidden file in your home directory) and restart.


Good call.   I removed .gconf and rebooted, and the functionality I described worked again.   However, it's broken again.   Evidently there's some process I keep running that is causing this to happen.   Something tells me it's snes9x (SNES emulator).   

In any case, thank you very much.

---

### Post by QCompson on 2008-08-10
> **fredmv said:**
> Good call.   I removed .gconf and rebooted, and the functionality I described worked again.   However, it's broken again.   Evidently there's some process I keep running that is causing this to happen.   Something tells me it's snes9x (SNES emulator).   

In any case, thank you very much.

I bet it is.  The very same behavior happens to me after I use snes9express.

---

### Post by euchrid33 on 2008-12-05
Yeah, snes9express does the same for me.  Is there any sort of fix for this?  I like it, and I can't make zsnes work on my system, but I really don't like this bug.

---

### Post by joepastafari on 2009-03-15
I just had this same problem with snes9express among others (joypad issues), and zsnes is acting up as well.  However I think I finally found my favorite snes emu for ubuntu, snes9x-gtk.  Not only does it not cause this issue, but everything else works awesome, including network play.  Give it a try, I doubt you'll be disappointed.
[http://www.snes9x.com/phpbb2/viewtopic.php?p=22874](http://www.snes9x.com/phpbb2/viewtopic.php?p=22874)

---

