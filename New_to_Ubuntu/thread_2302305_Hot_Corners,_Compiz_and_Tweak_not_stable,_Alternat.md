---
title: "Hot Corners, Compiz and Tweak not stable, Alternative?"
date: 2015-11-09
forum: New to Ubuntu
---

### Post by greentea2 on 2015-11-09
Hi all, 


First of all, I am really still wondering why at this stage there are still no hot corners out of the box built in Ubuntu. 


For now I have setup Compiz and Tweak, but they are not stable and do not work anymore after rebooting.


Is there any other and better way or app to setup the corners?


Really would appreciate any comments or help! 


Thanks! ;)

---

### Post by grahammechanical on 2015-11-09
What version of Ubuntu are you using? I think that Compiz Configuration Settings Manager (CCSM) and Unity Tweak tool are examples of community development. I do not see them as Canonical products. 

Besides, when Mir becomes the default compositor on Ubuntu instead of the X server then tools like CCSM and Unity Tweak will no longer work. The same would be true if it was intended to switch to a Wayland compositor. It has taken a long time but changes are a coming. What we get "out of the box" with Unity 8 will be different from what we get with Unity 7.

Regards.

---

### Post by howefield on 2015-11-09
> **greentea2 said:**
> Is there any other and better way or app to setup the corners?

There is a reason that compiz-settings-manager is not included in the default Ubuntu installation, and also that there is a warning to accept when you do install and then run it, it has a considerable number of options that may or may not break your system over and above the official Unity plugin. Unity Tweak Tool however, as I understand it, is a completely different story in that it only functions as a gui wrapper to settings already available in your system, settings that can be accessed via the command line.

In other words, find the settings that unity tweak tool changes and you can probably change them in terminal. I do not use hot corners so can't give any better pointers than that. 

To be honest, I wouldn't be upset if something in the borked through using compiz settings manager, I'd almost expect it. But would be upset if unity tweak tool broke my system, I have never had that happen in literally, many hundreds of installations.

---

### Post by greentea2 on 2015-11-09
> **grahammechanical said:**
> What version of Ubuntu are you using? I think that Compiz Configuration Settings Manager (CCSM) and Unity Tweak tool are examples of community development. I do not see them as Canonical products. 

Besides, when Mir becomes the default compositor on Ubuntu instead of the X server then tools like CCSM and Unity Tweak will no longer work. The same would be true if it was intended to switch to a Wayland compositor. It has taken a long time but changes are a coming. What we get "out of the box" with Unity 8 will be different from what we get with Unity 7.

Regards.

Then I am really looking forward to Unity 8, ..._is there already a release date?_

Regarding Ubuntu, I've used both. LTS as dual boot and 15.10 on the VM. Cannot see any difference regarding this issue.

---

### Post by ssreddy555 on 2015-11-11
Both Compiz and Tweak tool are working perfectly on my 15.04 installation.

---

