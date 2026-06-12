---
title: "Flash objects &quot;bleed&quot; through separate tabs"
date: 2012-05-07
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2012-05-07
I have a semantics problem with this post. I'm not a computer whiz or at all technical. I don't know the words by which to accurately describe my problem. Please read on.

For about 2 to 3 months, Youtube and other Adobe Flash related objects bleed through to tabs open in Chrome. That sometimes they even bleed onto the desktop. That is to say: Flash objects, at times, become persistent. If I close one tab and open another, the object is still there, occupying screen real estate, but it doesn't belong there. I cannot show a screen print as the print shows the forward most screen and not the Flash object. This happens inconsistently.

I also have, as I type this Thread, a weakening of the pixels (or what-have-you) for the letters you are reading. The letters start to look like stencils, sort of.

This has been this way from 11.40 (Oneiric Ocelot) through 12.04 (Precise Pangolin)

---

### Post by efball3 on 2012-05-09
I'm seeing the same problem.  It's really annoying.
Google Chrome 18.0.1025.168  I see reports of firefox doing this too.
Ubuntu 11.10
Fvwm window manager.  So it's doing it on different window managers.
Nvidia Driver 280.13  (I'm pretty sure this is the problem).

[http://forums.freebsd.org/showthread.php?t=25848](http://forums.freebsd.org/showthread.php?t=25848)
says it's an Nvidia bug.

right click and disable hardware acceleration.  Reload the video.
Seems to work for now.

---

### Post by Mark_in_Hollywood on 2012-05-11
Some instruction:

Go to a Flash video object. That can be a Youtube vid or Vimeo, just as long as it's a Flash video or Flash based object on your monitor screen.

Right click on the video or object. Select "Settings" (no quotes on screen). Click on leftmost icon at bottom of Flash Player Settings windows. You will see a checkbox for Hardware Acceleration. Uncheck that box.

You are good to go.

Thank you efball3.

---

### Post by dgharmon on 2012-11-09
> **Mark_in_Hollywood said:**
> You will see a checkbox for Hardware Acceleration. Uncheck that box

That's not a solution, still happening on Ubuntu 12.10 quantal x86

---

