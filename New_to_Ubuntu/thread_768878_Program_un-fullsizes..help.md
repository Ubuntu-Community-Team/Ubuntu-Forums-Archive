---
title: "Program un-fullsizes..help?"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by pHreaksYcle on 2008-04-26
I am trying to play a game called Urban Terror for linux. It was working fine before but now when I open it up, it will not fullscreen, it makes the window borders as big as they can go and lags out.

So I have instead of fullscreen, a maximized window with an unresponsive game, keyboard still works however while this is happening.

Is there a hotkey to fullscreen or any other ideas I could try? Thanks!

---

### Post by pHreaksYcle on 2008-04-26
I can't understand why people respond to THIS fool and not me :P

[http://ubuntuforums.org/showthread.php?t=768686](http://ubuntuforums.org/showthread.php?t=768686)

Feeling kind of dejected, any ideas? 

Thanks

---

### Post by kestrel1 on 2008-04-26
Has anything changed on your machine? Did this happen after an update to the system or something similar.

---

### Post by mc4man on 2008-04-26
same advice - 
[http://ubuntuforums.org/forumdisplay.php?f=230](http://ubuntuforums.org/forumdisplay.php?f=230)
[http://ubuntuforums.org/showthread.php?t=651809&highlight=urban+terror](http://ubuntuforums.org/showthread.php?t=651809&highlight=urban+terror)

---

### Post by pHreaksYcle on 2008-04-26
No sir, nothing that I can think of, save installing codecs this morning. Even after that it worked, I'm at a loss. Looking for a fullscreen hotkey on google.
Thanks for your replies

---

### Post by Jared Norris on 2008-05-01
I had a real problem with this and Urban Terror myself

I found help on another thread:

[http://ubuntuforums.org/showthread.php?t=769020](http://ubuntuforums.org/showthread.php?t=769020)

From that thread:

> **Melcar said:**
> Someone should really sticky an information thread on this.  Currently, you can't use any form of desktop composition effect (KDE/XFCE transparency included) with any form of 3D/2D accelerated rendering.  DRI2 fixes this, but it's not officially out yet.  The only real option one has if he really wants to keep using Compiz and still be able to render with opengl and/or Xv is to get an nvidia card and use the proprietary drivers, since the nvidia drivers act differently.  Again, this is not an ATI problem; every single driver out there (be it proprietary or open source) is affected by this (with different degrees of severity).

I followed the next post as a workaround until this DRI2 is officially out:

> **psayre23 said:**
> Same issue on a 9700 mobile. I installed fusion-icon and change the window manager to metacity when I want to run a 3d app. If you are gaming, you'll most likely want to turn off compiz anyways, so it is handy.

Agreed, this is a workaround...but it is better then having flickering in-game, and should boost your frame rates a bit. And stick_request++;

sudo apt-get install fusion-icon

fusion-icon

Hope that helps, it works for me.

---

### Post by ergonomicben on 2008-05-04
Thanks for finding out a work-around, this had been really bugging me!
So does anyone know when DRI2 is going to be out officially? I assume it will come through an update sometime in the near future?

---

### Post by ergonomicben on 2008-05-22
big bump here! so the question remains, when is DRI2 out and will it come through an update?

Although after a bit of searching i'm not conviced this will solve my problem when it does indeed come out. I currently use a nvidia 7600gt with the restricted drivers and i have the same problem as the op. will DRI2 have any affect? or is it only for ATI cards....i'm getting confused!!:confused:

---

