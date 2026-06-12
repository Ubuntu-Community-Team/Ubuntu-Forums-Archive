---
title: "[SOLVED] When opening folder top bar disappears"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by Lizard787 on 2008-05-18
Hi
When I open a folder any folder the top and bottom bars disappear all of the sudden.And they don't come back unless i exit out of the folder.

---

### Post by garyedwardjohnston on 2008-05-18
Very strange.

I will need a lot more information to diagnose.

---

### Post by Lizard787 on 2008-05-18
Well im using hardy heron 8.04 used the dvd image. It is a toshiba satellite P105-S6024 laptop. Has an Intel 945GM graphics card running on external monitor internal cracked so i just took it off and am using the vga port (1024x768 ) resolution max.
Whenever I go to say places>Home folder or any folder when it opens the top and bottom bars disappear. When i alt-tab to say firefox they come back i've tried right clicking and resizing but no luck.
Just ask me if you need anymore information.

---

### Post by AstralliS on 2008-05-18
Do you use effects? Do you have installed Emerald?

---

### Post by HotShotDJ on 2008-05-18
> **AstralliS said:**
> Do you use effects? Do you have installed Emerald?This looks like a problem with Compiz.  Go to System --> Preferences --> Appearance --> Visual Effects and set it to "none" and see if that corrects the problem.

---

### Post by Lizard787 on 2008-05-18
Ive never heard of emerald. So i don't think so. And turning off effects didnt work either.
All i have installed is maybe an updated alsa sound wasnt working never did get it fixed. gFTP, Wine, gmount-iso.

---

### Post by HotShotDJ on 2008-05-18
> **Lizard787 said:**
> Ive never heard of emerald. So i don't think so. And turning off effects didnt work either.
All i have installed is maybe an updated alsa sound wasnt working never did get it fixed. gFTP, Wine, gmount-iso.
Emerald is required to get Compiz to work with KDE.  It shouldn't be a factor here.  Try this... use Alt+F2 and type in ```
metacity --replace
``` to completely turn off Compiz.  I'm 99% sure that Compiz is the problem... I'm just not yet sure why.

---

### Post by Lizard787 on 2008-05-18
Screen flashed but the bars still were gone.

---

### Post by ryanhaigh on 2008-05-18
Strange issue but it seems others have experienced it as well. [This thread ]("http://ubuntuforums.org/showthread.php?t=663422")contains a solution which has worked for others, hope it helps.

Personally I didn't even know nautilus had a fullscreen mode but in firefox and some other apps you use the F11 key to toggle fullscreen, perhaps nautilus has the same feature although I didn't find any info in my brief google search.

---

### Post by Lizard787 on 2008-05-18
Thanks it seems to be working now!

---

### Post by HotShotDJ on 2008-05-18
> **Lizard787 said:**
> Screen flashed but the bars still were gone.Ok. In that case, it may not be a compiz issue. I've looked at the thread that ryanhaigh referenced and that seems like a reasonable hypothesis.  Go ahead and give it a try.  If it works, you can mark this thread as solved.  If not, I've got one more thing to try before admitting defeat. :)

---

