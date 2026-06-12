---
title: "Python - PyGame collison"
date: 2011-12-16
forum: Programming Talk
---

### Post by catmanjon on 2011-12-16
Hey guys, I've been working with Python for a couple months now, and I just picked up the basics up PyGame yesterday. I've been lurking for a while, and almost every post I've seen has been solved.

I came to get some help with the collision in my game (or whatever you'd like to call it). I believe I have the detection set up properly, I believe, but when I move my Player object towards my Box object that is supposed to stop the Player from moving through it, it does. The problem is when I move the Player object against on KEYDOWN it slides either up or down depending on where you hit it, and when you release the key it has jumped back the same number of pixels as velocity. My wall collision works perfectly fine, but I don't know what I did with my Player to Box collision wrong.

If this didn't make any sense, and/or you'd like to help me with my problem here is my code attached below. If you solve the problem, please let me know what I did wrong so I can prevent this in the future!

Thanks a tonne,
Jonathan

---

### Post by gmargo on 2011-12-16
I don't entirely agree that your wall collision code is correct.  Try changing the "speed" parameter to a non-multiple of the window size, for example "9" instead of "10".  Then you'll see problems pop up.

The box collision is more complicated.  I had to keep track of which direction I was moving in, in order to apply the proper correction.  In doing so I had to adjust how your event loop worked.

See the attached code:

---

### Post by catmanjon on 2011-12-16
> **gmargo said:**
> I don't entirely agree that your wall collision code is correct.  Try changing the "speed" parameter to a non-multiple of the window size, for example "9" instead of "10".  Then you'll see problems pop up.

The box collision is more complicated.  I had to keep track of which direction I was moving in, in order to apply the proper correction.  In doing so I had to adjust how your event loop worked.

See the attached code:

Nevermind

---

### Post by mandza on 2011-12-17
catmanjon if you write how did you solve problem it would be more helpfull.

---

