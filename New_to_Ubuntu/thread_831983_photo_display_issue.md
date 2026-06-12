---
title: "photo display issue"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by flyingsolo on 2008-06-17
My photos display as though they were vertically squished--not a lot, just enough to be noticeable and annoying.  Probably this has to do with display drivers but I haven't found the solution, so help please!
computer is Dell inspiron 6400 (also known as e1505 I believe) with ATI radeon x1400 card currently using the ATI accelerated graphics driver (proprietary).
Probably everything on my desktop is similarly squished but I don't seem to mind/notice it with typing, browsing or desktop icons etc. but you do really see it when looking at photos, video.
Thanks.

---

### Post by phidia on 2008-06-17
Maybe this is a monitor issue? Take a look at-find your monitor's vert & horz sync specs and then compare that to what is listed in /etc/X11/xorg.conf. If there is a big difference then edit your xorg.conf to reflect the monitor specs.

---

### Post by flyingsolo on 2008-06-17
Thanks for the suggestion--this is a laptop & I'm not sure of the monitor horz/vert sync specs or where to find them! (I'm still a newb!)

---

### Post by phidia on 2008-06-17
I don't have much experience with ATI cards so I'm referring you to a thread [here]("http://ubuntuforums.org/showthread.php?t=221320") which has several links to guides. Hope that helps.

---

