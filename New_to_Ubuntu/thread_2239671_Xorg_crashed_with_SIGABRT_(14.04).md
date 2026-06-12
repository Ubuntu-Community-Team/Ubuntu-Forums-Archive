---
title: "Xorg crashed with SIGABRT (14.04)"
date: 2014-08-15
forum: New to Ubuntu
---

### Post by Jamie_Dexter on 2014-08-15
Hello all, first post! 

I am running Ubuntu 14.04, downloaded from the Ubuntu site about a week ago and installed onto my fairly new beastly gaming PC. Everything runs perfectly fine until the current program I'm using hangs, then moments later the keyboard stops working, and moments after *that* the mouse hangs. The computer remains in a completely hung state, sometimes with some visual artefacts, until I press the Reset button. Using Alt + PrtScn + R, E, I, S, U, B per Stack Overflow doesn't work (I suspect as the keyboard is hung) and so the Reset button is the only recourse.

I am brand new to Ubuntu and Linux in general; at the time I had open Chrome (Gmail, GitHub, mebbe an SO page or two) and Terminal, in which I was running a Composer update. This crash always seems to happen with every run of Ubuntu, always about 10-20 minutes after booting.

My machine is water-cooled and usually runs Windows 7 for many, MANY gaming hours without the slightest hiccup. I received the "Xorg crashed with SIGABRT" message upon rebooting. When it happens again I'll post the precise details, but does anybody have a thought as to why this would be happening?

---

### Post by ManiacDan on 2014-09-22
I experience this exact same issue on a laptop that ran 12.04 with absolutely no issues for 2 straight years.  I'm seriously considering downgrading to 12.04 if this can't be figured out.  

Does anyone know why this happens?  It seems to happen any time there's a momentary hiccup in an application, maybe something that would trigger the compiz "dim hung applications" plugin.  I believe this may be the case because Chrome causes this problem far more often than Firefox, and imgur causes it after about 4 minutes (imgur is a memory hog, and chrome is unstable).

Jamie, if this is still happening, try to remember which apps you're using when this happens.  Maybe switch away from that app temporarily and see if that helps.

---

### Post by ManiacDan on 2014-09-23
**Edit: ** Jinxed myself.  I just experienced this crash again.  I use this computer for work, it can't lock up at random.

---

### Post by d4m1r on 2014-09-23
The problem with SIGABRT crashes are find that not only are they random, but that is a "general" error message that often doesn't provide additional researchable troubleshooting behavior.

If Xorg is what is crashing, it might be something related to your video cards/video card drivers. Maybe post the full specs of what both of you are running and if there are any similarities, you can go from there?

---

