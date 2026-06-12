---
title: "Google Earth logs me out too"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by jerrywo on 2008-08-26
Previous posts suggest this is a kernel problem.  I don't know about that.  When I launch GoogleEarth, it immediately crashes and logs me off the computer.  I've uninstalled and installed previous versions (4.2) and the same thing happens.

Some mention was made about editing the config script.  In order to get Ubuntu to start, i had to append "noapic" to one of the lines.
any hints?
jerry W

---

### Post by Linux_Man on 2008-08-26
What happens when you run it from the terminal? Any error messages it produces would be helpful.

---

### Post by captgadget on 2008-08-26
I found this to be a graphics problem.

---

### Post by Crafty Kisses on 2008-08-26
Like back to the login screen?

If that's the case then X is crashing for some reason.

---

### Post by jerrywo on 2008-08-27
The same thing happens when I try to run it from the Terminal.  As soon as I hit the return key, boom, it's down.  I get a little flash of a black screen for about one second with some scripts - it goes by too fast to read.

and yes, it just might be video.  I did notice some "stuttering" (for lack of a better word) of a desktop icon a few days ago when I tried to drag it to the trash.  In fact the display froze up for a period of time.

There was a busted file, a link IIRC, in my first GoogleEarth Install.  That was the start of my woes.
jerry

---

### Post by billgoldberg on 2008-08-27
> **jerrywo said:**
> Previous posts suggest this is a kernel problem.  I don't know about that.  When I launch GoogleEarth, it immediately crashes and logs me off the computer.  I've uninstalled and installed previous versions (4.2) and the same thing happens.

Some mention was made about editing the config script.  In order to get Ubuntu to start, i had to append "noapic" to one of the lines.
any hints?
jerry W

Sounds like [X]("http://www.x.org/") is crashing.

If you have compiz fusion running, turn it off before using Google Earth (use the command "metacity --replace").

---

### Post by jerrywo on 2008-08-27
Nope, I don't have Compuz Fusion running.


Any logs I can look at?
jerry

---

