---
title: "firefox 3 display problem"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by Knacker on 2008-06-22
hi, 
firefox has spontaneously begun acting strangely. i say spontaneously, becuase i can't think of anything i changed between the time that it was working well and now, when it is not. the problem has to do with some kind of conflict between compiz/visual effects and firefox. the symptoms are as follows: 
1) when i open firefox, it opens with everything but the title bar (i.e. no close, maximize, buttons). 
2) firefox also covers everything (including awn and the gnome toolbar/launchbar or whatever you call it).
3) when i begin to enter something into a text field on a web page (say, typing the words into a google search, or the search field at the top of the ubuntu forum page), the screen flashes..). 
4) when i turn off desktop settings, everything is fine and firefox displays as normal, no flashing.

Hardy Heron, all updates installed. latest nvidia driver from nvidia web-site: 173.14.09. (The regular ubuntu "proprietary driver" causes a whole different, worse set of problems.)

I know that's a lot, but any ideas anyone?

many thanks in advance!

---

### Post by AndThenWhat on 2008-06-22
It sounds like the video driver you're using doesn't play nice with Compiz.  You could try logging into the Gnome Failsafe session and starting Compiz, I guess?  Also, maybe play with the resolution or check out System -> Administration -> Hardware Drivers.  Just ideas on all of those, don't know if they will do much.

---

### Post by aktiwers on 2008-06-22
I just had the exact same problem.
I tried lots of things and non worked. I found it was because Firefox was "too big for the screen".

After I hit F11, 2 times, it let me drag the upper right corner and resize the window so it went back to normal.

Or try with ALT+F8

---

### Post by Knacker on 2008-06-22
> **aktiwers said:**
> I just had the exact same problem.
I tried lots of things and non worked. I found it was because Firefox was "too big for the screen".

After I hit F11, 2 times, it let me drag the upper right corner and resize the window so it went back to normal.

Or try with ALT+F8

F11 worked! :D thank you so much! 
I was worried i was in for another epic struggle with nvidia drivers. 

odd problem... glad such an easy fix. 

thanks again, guys!! :guitar:

EDIT: ah man! i've gotta do F11 twice every time i open FF!? hope this fixes itself as spontaneously as it broke...annoying!
EDIT: okay...no more F11: fixed for real now. thanks again!

---

### Post by alienexplorers on 2008-06-22
You need this line added to the screen section of your xorg.conf file:
> Option         "AddARGBGLXVisuals" "True"

---

### Post by lilmo037 on 2009-01-18
> **Knacker said:**
> F11 worked! :D thank you so much! 
I was worried i was in for another epic struggle with nvidia drivers. 

odd problem... glad such an easy fix. 

thanks again, guys!! :guitar:

EDIT: ah man! i've gotta do F11 twice every time i open FF!? hope this fixes itself as spontaneously as it broke...annoying!
EDIT: okay...no more F11: fixed for real now. thanks again!

I am having the same problem and figured out the F11 trick, but how did you fix it for real?  Can you dumb the explanation down for a new Windows convert?  :???:

---

