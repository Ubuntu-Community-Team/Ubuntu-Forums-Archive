---
title: "Window decorator missing"
date: 2011-09-18
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by hebetude on 2011-09-18
So when I login to Unity, Gnome3, Gnome2, Unity2d I have no window navigator.  I thought this was something fubar with the upgrade and this seems to be the case.  I created a new user account and it starts just fine with window decorations.  

However, the account existing before the upgrade opens with nautilus as the top bar, and nothing else.  I can't use Alt+F2 or Alt+F1 (hotkeyed to start a new terminal).

I've tried launching a terminal session then calling 'gtk-window-navigator --replace' 'compiz --replace' etc. nothing fixes it.  I've also tried moving most of my config files in my home directory to other locations, can't seem to find the issue here.

**UPDATED WITH ANSWER**
My issue seemed to be settings in my 11.04 installed account.

It was not enough to remove any of the gnome config files .gconf, .gconfd, .gnome2, .gnome2_private in fact you can leave those files as is.  The issue is with something in my .local directory.  Remove or move this somewhere else then look around for what may be breaking your system.

Thanks for help,

---

### Post by awam66 on 2011-09-18
I've had this problem for a long time. But only on Unity3D 64bit. 2D and Gnome work fine. It seems to be a problem with nvidia drivers as far as I an see. Sorry not much help but there are bug reports for it somewhere perhaps someone else can point us in the right direction. I have tried all the suggestions to fix it but none work.

---

### Post by BaddestCross on 2011-09-19
I had this problem as well.  Your Unity plugin has been disabled.  Launch ccsm from the terminal (ctrl-alt-t) and re-enable it answering 'Yes' to every conflict pop-up that appears and it will come back online.

---

### Post by hebetude on 2011-09-19
> **BaddestCross said:**
> I had this problem as well.  Your Unity plugin has been disabled.  Launch ccsm from the terminal (ctrl-alt-t) and re-enable it answering 'Yes' to every conflict pop-up that appears and it will come back online.

This would probably help people with Unity problems, but did not resolve my Unity or Gnome 3 problems.  I did notice a ton of Crashes while resolving the conflicts.

---

### Post by hebetude on 2011-09-19
So, I logged into the working user, clicked switched user, logged into the pre-existing account and got Unity 2d and Gnome classic to run.  Gnome classic informs me of an error with my video drivers and has started in fallback mode.  I tried some WebGL sites and they definitely work and better than on Ubuntu 11.04.  

So I'm going with this did resolve some issues, but maybe do the workaround above on a working user just to be sure then switch while that user is still logged in.

---

### Post by hebetude on 2011-09-22
For those wondering, this fixed 2d ie Ubuntu 2d and Gnome classic.  3D fancy versions still fail to load on existing account, but work fine in a new account.

---

