---
title: "Occassional text display errors"
date: 2013-01-26
forum: New to Ubuntu
---

### Post by BrianV on 2013-01-26
I am reestablishing ubuntu 12.04.1 on a new-to-me desktop with an Intel core 2 duo CPU chip, onboard graphics, and Asus motherboard (I don't recall how to query the details). It is dual boot with WinXP.

In XP the display seems normal, so I don't suspect a hardware problem.

In ubuntu there is a rendering problem with the display that affects many applications, so I think has to do with the graphics handling (driver?). What happens mostly is that pixels within displayed characters are missing. It is most evident with bold text or large fonts, where horizontal lines of pixels will be missing - not necessarilly all the way across a character. The problem also shows up on solid blocks of colour or on icons, but perhaps to a lesser extent. In any case, the problem is visible only occassionally. When the problem shows up on a window, all instances of the character will be affected the same way.

Is anyone else seeing this?

Is there some diagnostic approach to better understand what is going on?

---

### Post by Impavidus on 2013-01-26
The problem affects everything stored in video memory (like letters, they are cached there by the application) and things stored at the same location in memory (different instances of the same character in the same font and size in the same application) are affected in the same way, so it's definitely some kind of video memory corruption, most likely caused by a buggy video driver (or at least, not optimal for your hardware).

Check for available drivers (settings>additional drivers or something like that, I'm not sure how it's called on your ubuntu version).

Edit: I saw you had a different thread on this subject already and someone already make my comments about drives. Best to continue this discussion in the other thread only. Other thread: [http://ubuntuforums.org/showthread.php?t=2108492](http://ubuntuforums.org/showthread.php?t=2108492)

---

### Post by BrianV on 2013-01-27
> **Impavidus said:**
> The problem affects everything stored in video memory (like letters, they are cached there by the application) and things stored at the same location in memory (different instances of the same character in the same font and size in the same application) are affected in the same way, so it's definitely some kind of video memory corruption, most likely caused by a buggy video driver (or at least, not optimal for your hardware).

Check for available drivers (settings>additional drivers or something like that, I'm not sure how it's called on your ubuntu version).

Edit: I saw you had a different thread on this subject already and someone already make my comments about drives. Best to continue this discussion in the other thread only. Other thread: [http://ubuntuforums.org/showthread.php?t=2108492](http://ubuntuforums.org/showthread.php?t=2108492)
I will mark this thread solved and use the other one.

---

