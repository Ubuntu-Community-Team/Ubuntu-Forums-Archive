---
title: "x server issue"
date: 2012-01-23
forum: New to Ubuntu
---

### Post by guitarguy2112 on 2012-01-23
Alright. I come from an earlier post with display drivers...

In order for me to install the nvidia drivers, I had to install the libc headerfiles, after that was done I did this:
sudo /etc/init.d/gdm stop

This way I can install the drivers, as the display must be turned off...

Well, the thing is, it gives me 4 messages. I would wait for about 10-15 minutes, and there is no command line. I had seen the command line before(before I installed the libc headerfiles), and now there is none. 

It just doesn't show up at all. Any advice? thanks in advance!

EDIT:

I am using 8.04 64bit

---

### Post by Gone fishing on 2012-01-23
You’re compiling the drivers rather than using the ones in the repository?

Why not just use the additional drivers utility?

---

### Post by guitarguy2112 on 2012-01-23
> **Gone fishing said:**
> You’re compiling the drivers rather than using the ones in the repository?
 
Why not just use the additional drivers utility?
 
Additional drivers utility? I can't think of it off the top of my head(I'm at work now), but if I go into system tools and all that, and look at the proprietary drivers it shows none.
 
What's the command for the repositories for these nVidia drivers? It's a GTS 450. According to nVidia's website it says I need to do all this stuff...

---

### Post by Miljet on 2012-01-23
> Why not just use the additional drivers utility?

Probably because the OP is using 8.04, which is no longer supported.

---

### Post by Gone fishing on 2012-01-23
> Probably because the OP is using 8.04, which is no longer supported. 

Good point - you need to use either 10.04 or 12.04 which are currently supported, then it should be as easy as running the additional driver utility.

---

