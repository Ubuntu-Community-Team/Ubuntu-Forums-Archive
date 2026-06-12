---
title: "Lost launcher, dash top bar - how to restore?"
date: 2011-10-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by asampaleanu on 2011-10-08
Hi,

I upgraded from natty to oneiric and in fiddling around with various things, I managed to muck up Unity such that now I don't have a launcher, dash or the top bar (well, actually there is a menu bar, but it just shows the Nautilus menu and doesn't change when other apps have focus). Also, there are no indicator icons.

Can anyone give me a clue as to how to restore the disappeared UI components? I've tried to remove and re-install both Unity and lightdm, but that didn't do it. I did this while using Unity, from a tty - should I be using Unity2D when I try to remove/reset Unity?

Any help would be much appreciated.

Adrian

---

### Post by effenberg0x0 on 2011-10-08
Hey,

Switch from the Ubuntu (3D) desktop to a VT using **Ctrl+Alt+F1** to F6
Login to the VT and run **DISPLAY=:0.0 ****/usr/lib/nux/unity_support_test -p** (to make sure your system current setup is able to use Unity).
In the VT, run **DISPLAY=:0.0 /usr/bin/ccsm &**
Switch back to the Desktop with **Ctrl+Alt+F7**

In CompizConfig Settings Manager, see that **Ubuntu Unity Plugin** is activated. Even deactivating/reactivating it might help.
Either Unity Launcher and panel will immediately appear or ccsm will crash (it is unstable when activating the plugin). You might have to try it a couple times.

Back to the VT you had just used, run **sudo service lightdm restart**
Login, check if session is looking OK

If not, back on the VT, run **unity --reset**
**Ctrl+Alt+F7** and Check your session.

If not, Back to the VT you had just used, run **sudo service lightdm restart**
It's sort of a loop until it starts working OK. 

Regards,
Effenberg

---

### Post by asampaleanu on 2011-10-08
Thanks for trying to help out. When I try to run unity_support_test -p, I get:

Error: unable to open display.

I tried to do the other steps even so, but they didn't restore the missing UI elements. In CCSM, checking/unchecking the Unity plugin didn't crash CCSM (or do anything else other than display a dialog about conflicting key and edge bindings). Also, is it normal that running 'unity --reset' doesn't come back to the prompt (I have to ctrl-c out)?

BTW, in case it helps, I'm running with dual monitors.

Are there any user settings involved that I could just wipe to 'reset' things as they were? Should uninstalling the packages I mentioned and re-installing not do this?

---

### Post by dmoconnell on 2011-10-08
Stupid question + my 2cents 
I actually had this problem as well (upgrade went fine then the next day no launcher+top menu bar just Nautilus) I had noticed there we're updates. So logged out and logged in via Ubuntu 2D (which was still working) and ran updates (there were some for Unity i noticed) and poof Unity decided to work again in Ubuntu (Normal mode not 2d)
My stupid question is this :Is your system up to date. If there is updates (particularly for unity) update, for some reason a more knowledgeable tech might know that fixed it for me. 
Hope this helps
Dm

---

### Post by asampaleanu on 2011-10-08
Well, after switching back to nvidia-current (from nvidia-current-updates) and re-booting, I still had the missing elements, but something I did afterwards (tried unity --reset in a VT, enable/disable unity plugin in compizconfig while in unity 2D) restored things when I finally logged back in with Unity 3D.

I now remember that there were some graphical artifacts (the zoom in-out region of the workspace switcher) that made me attempt the driver switch in the first place.

Thanks all for the suggestions, in any case.

How do I mark this problem as solved? I tried to edit the title of the first post, but only the thread view title changed, and not the forum view.

---

### Post by cariboo on 2011-10-08
> How do I mark this problem as solved? I tried to edit the title of the first post, but only the thread view title changed, and not the forum view.

Only the op of the thread can add the solved tag. You should see Mark this thread as solved under thread tools.

---

