---
title: "Ubuntu Stuck in 800x600 While Set To 1680x1050"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by Ninelivez on 2008-05-19
I dunno what happened, I just restarted my computer, then it said that Ubuntu couldn't find my Video Card and loaded into low graphic mode. I chose to configure my settings in that screen and chose the resolution of my PC, 1680x1050. But now when it loads up, the screen itself is in 1680x1050, but...it isn't. I need to use the mouse to push on the edges of the screen to move it around to see everything. I dunno what to do, any ideas?

I hope that made sense, I am just as confused as you are.

---

### Post by Ninelivez on 2008-05-19
Here's what its showing up as in my Nvidia Configuaration Window. Might help explain this a little better.

[img]http://xs127.xs.to/xs127/08212/what709.jpg[/img]

---

### Post by RequinB4 on 2008-05-19
I'm thinking this might be a driver problem.  On the "low graphics mode" screen, try pressing configure and manually picking the driver you were using.  If you don't know or nothing works, run the VESA drivers and you may have to get the (proprietary?) drivers manually.

What video card do you have, and can you think of anything that might have caused it?

Edit:  Also, you really didn't have to make 2 posts here and one in the other thread :P :guitar:

---

### Post by Living2007 on 2008-05-19
> **Ninelivez said:**
> I dunno what happened, I just restarted my computer, then it said that Ubuntu couldn't find my Video Card and loaded into low graphic mode. I chose to configure my settings in that screen and chose the resolution of my PC, 1680x1050. But now when it loads up, the screen itself is in 1680x1050, but...it isn't. I need to use the mouse to push on the edges of the screen to move it around to see everything. I dunno what to do, any ideas?

I hope that made sense, I am just as confused as you are.
you have may blown the res too big, either try a lower res, or update the nVidia Ubuntu Driver or punch in a code.

Ive forgoten the code, I reply back when I found it (unless someone tells you it)

---

### Post by Ninelivez on 2008-05-19
Thanks for the replys. I dunno how to get back to that screen that tells me it is going to load in Low Graphic Mode. It only did it once, everytime I restart now, it doesn't come up. The only resolutions I can choose are ones that are way too small, doesn't even let me get up to the real resolution. 

I'll try disabling the nvidia driver and re-enabling it. 

I'm using a Nvidia 8800GT 512mb.

And this is all coming from a VERY New Ubuntu user >.<

---

### Post by Ninelivez on 2008-05-19
Sorry for the double post.

I disabled the Nvidia drivers and restarted, the resolution was fine. Then I re-enabled it and restarted, now its back to being goofy. I can disable it until I figure out whats wrong I guess, but its still weird lol.

---

### Post by RequinB4 on 2008-05-19
:) for future reference, there is an "edit" button at the bottom of each post you make that can save people a lot of bandwidth.

You disabled the nvidia drivers, and it was fine? Was it fine as in 800x600 fullscreen and not weird, or as in the resolution you want?  What drivers are you using so that it works "fine?"

P.S: If it ain't broke don't fix it :)

---

### Post by Ninelivez on 2008-05-19
Oh doh! Forgot about edit just kinda flustered getting everything up to date and whatnot, sorry!

Oh, well I just disabled it, restarted, and it was in the 1080x1050 resolution. When I reinstalled the driver and rebooted, it went back to being funky, everything being huge, and blurry, me having to "push" the screen around with my mouse to see everything, etc.

I just worry because I am wondering if I needed that driver to run a few games on here. (I know there aren't a ton, but I know WoW works well and I was hoping to play that without booting into windows).

---

### Post by RequinB4 on 2008-05-19
> **RequinB4 said:**
> P.S: If it ain't broke don't fix it :)

Everything's fine with the non-proprietary drivers, and the thread is solved.  If you start WoW in Wine and you get an error, that's a seperate issue that probably can be easily solved by a proper 3-D driver install.

Also, your video card is relatively new.

---

### Post by sirgogo on 2008-05-19
Hello,

I have a NVidia8600 GT myself. Ubuntu has problems with the 8600 - 8800 series for some reason. Resolution:

1. Install Ubuntu proprietary drivers.
2. Install envyNG ([http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html))
3. Reboot and experience low graphics.
4. Run envyNG in either text or GUI mode. Remove old nVidia driver first.
5. Now reinstall new NVidia driver. If errors come up concerning dpkg, do what it says and resume installation of the NVidia driver.
6. Enjoy!

Good luck and tell me how it goes!

---

