---
title: "Multi monitor display help! (hardy 8.04)"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by cinohpa on 2008-09-06
** before you read any further, note that I actually fixed the problem myself but at the end I have a different problem so skip to the bottom for my new question and the answer to this one! ** So I'm running ubuntu with two monitors. The 1680 x 1020 lcd laptop monitor, and a 1920 x 1200 .  Under the applications >> other >> screens and graphics I have: 

Model: lcd panel 1920 x 1200 
Resolution: **1600 x 1200** and not the same resolution as my monitor. When looking through the options of possible resolutions 1600 x 1200 is the highest available resolution and because it isn't native everything just looks funny. (I have the same problem with what's displayed on my other monitor, just change the numbers.)

The other strange thing is that the images displayed on my monitor take up more than the whole screen so when I move towards the edges the image on my monitor moves to show the parts of my screen that "don't fit" 

What do I have to do to resize everything properly so my monitors can be at native res and nothing is cut off/forced to mouse over to to reveal?

Thanks a lot.

** Answer: There is a box in the window where you select which monitor is installed i.e. "1920 x 1200 lcd panel" and that box has written next to it "Wide screen monitor" unless you click that box, even if you have selected a wide screen resolution, ubuntu will not recognize your res properly. **

** My new question: My desktop is perfectly stretched over the two monitors. Is there anyway to allow each monitor to display an image on it's desktop independently? Thanks. **

---

### Post by kjohansen on 2008-09-07
I assume by stretched you mean you set it up with two x servers using xinerma.


If so then no you can't set it up with two different images on the two desktops.

If you disable xinerma, and just have two x servers then yes this is possible, but there are downfalls to not using xinerma, such as an app started on one desktop cannot be moved to the other.

---

