---
title: "xserver crashes while watching videos"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by JohnGalt131 on 2008-11-16
Occasionally my xserver crashes: I get a bunch of vertical purple bars and after less than a second I am at the login screen. It happens when I watch certain avi files and when I use virtualbox running windows xp. I noticed that the update manager had an update for nvidia settings. This is weird because I do not have an nvidia card, I have intel. I wonder if Ubuntu thinks I am using nvidia. How could I check this?

Thanks!

---

### Post by MunkyJunky on 2008-11-16
I used to use Intel a while back - I had issues with it (running on Ubuntu 7.10, and 8.04). This was because (or I was told it was because) the Linux Intel graphics driver sucked at the time. I don't know if this is still the case, but if so that *may* be why.

---

### Post by JohnGalt131 on 2008-11-16
> **MunkyJunky said:**
> I used to use Intel a while back - I had issues with it (running on Ubuntu 7.10, and 8.04). This was because (or I was told it was because) the Linux Intel graphics driver sucked at the time. I don't know if this is still the case, but if so that *may* be why.

It worked perfectly, for 7.10 and 8.04.

---

### Post by binbash on 2008-11-16
did you try to change the video output at your video player preferences?

---

### Post by JohnGalt131 on 2008-11-16
> **binbash said:**
> did you try to change the video output at your video player preferences?

No. What's weird is that the same video will crash x over and over but if I use metacity instead of emerald/compiz it doesn't crash.

---

### Post by binbash on 2008-11-16
change the video output to X11 and report back if the problem still occurs

EDIT : you can also watch your movies with compiz enabled if you switch the output to X11

---

### Post by JohnGalt131 on 2008-11-16
> **binbash said:**
> change the video output to X11 and report back if the problem still occurs

EDIT : you can also watch your movies with compiz enabled if you switch the output to X11

I'm not sure I understand. What would the video go to if not X11. Also, how do I specify.

---

### Post by binbash on 2008-11-16
dude if you are using mplayer, go the player's preferences there is video output there.Select X11.or VLC do same.

---

