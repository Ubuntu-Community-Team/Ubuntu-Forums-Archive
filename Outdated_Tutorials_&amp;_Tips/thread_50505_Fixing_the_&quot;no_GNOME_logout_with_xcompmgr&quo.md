---
title: "Fixing the &quot;no GNOME logout with xcompmgr&quot; problem"
date: 2005-07-20
forum: Outdated Tutorials &amp; Tips
---

### Post by Simon K on 2005-07-20
So, I decided to take some of all this X.org visual sweetness I've been hearing so much about for a spin. I managed to get it all working -- or, at least, the approximation of "working" it gets on my ATI graphics card.

But the big problem -- which I see that several people in the forums have been hitting -- was that GNOME's Log Out dialogue never appears when I hit the "Log out" menu button. The workaround usually suggested is to simply hit enter, since the dialog is still there, and in focus, but invisible. However, that seems a bit silly, so I found a somewhat more elegant workaround:

In *gconf-editor*, go to */apps/gnome-session/options*. You'll see a checkbox for the option *logout_prompt*, which is enabled by default. Disabling this will make GNOME log out without asking you for confirmation (and thus, never bring up the Amazing Invisible Blocking Dialogue), which is pretty much functionally equivalent to only being able to press Enter for "yes" anyway. I speculate that the cause of the problem is the unusual behaviour of the Log Out dialogue, in that it darkens the screen with a fade. If it was possible to configure it to **not** do that, I believe we'd be able to use xcompmgr and still get our Log Out dialogue. But in lieu of such an option, the above workaround seems like the next best thing.

I ended up not using xcompmgr anyway, though. At the moment, it seems slow and buggy (at least on ATI hardware), but I'm looking forward to seeing what the X.org people will make out of this one. Until then, though, the above workaround should get a sane GNOME logout for those of you who want xcompmgr.

Cheers,
Simon

---

### Post by poofyhairguy on 2005-07-20
[QUOTE=Simon K]So, I decided to take some of all this X.org visual sweetness I've been hearing so much about for a spin. I managed to get it all working -- or, at least, the approximation of "working" it gets on my ATI graphics card.

But the big problem -- which I see that several people in the forums have been hitting -- was that GNOME's Log Out dialogue never appears when I hit the "Log out" menu button. The workaround usually suggested is to simply hit enter, since the dialog is still there, and in focus, but invisible. However, that seems a bit silly, so I found a somewhat more elegant workaround:

In *gconf-editor*, go to */apps/gnome-session/options*. You'll see a checkbox for the option *logout_prompt*, which is enabled by default. Disabling this will make GNOME log out without asking you for confirmation (and thus, never bring up the Amazing Invisible Blocking Dialogue), which is pretty much functionally equivalent to only being able to press Enter for "yes" anyway. I speculate that the cause of the problem is the unusual behaviour of the Log Out dialogue, in that it darkens the screen with a fade. If it was possible to configure it to **not** do that, I believe we'd be able to use xcompmgr and still get our Log Out dialogue. But in lieu of such an option, the above workaround seems like the next best thing.

I ended up not using xcompmgr anyway, though. At the moment, it seems slow and buggy (at least on ATI hardware), but I'm looking forward to seeing what the X.org people will make out of this one. Until then, though, the above workaround should get a sane GNOME logout for those of you who want xcompmgr.

Cheers,
Simon[/QUOTE]


The reason the logout screen is screwed (and xcompmgr crashes an ass load in Gnome) is that Metacity has its own (crappy) compositor that fights with xcompmgr. The only way around it is to compile Metacity without its compositor (I have tried and failed at that for hours. I would pay $20 for a good how to that told me how to do that as long as it actually worked).

Now I use XFCE more because it lacks it compositor by default, and crashes less with xcmopmgr on.

Of course, xcompmgr is a dead end. Its poor perfomance on everything not Nvidia combined with the fact that Metacity is developing its own compositor (luminocity) means that xcompmgr is just a temporary fix.

Kind of sad, seeing that its fading trick will probably die with it....all the developers care about is transparancies....

---

