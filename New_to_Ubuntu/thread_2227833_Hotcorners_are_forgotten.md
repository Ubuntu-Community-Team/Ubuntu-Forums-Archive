---
title: "Hotcorners are forgotten"
date: 2014-06-04
forum: New to Ubuntu
---

### Post by smirnich on 2014-06-04
Hi! I have used the Unity Tweak Tool to set the top right corner to show available workspaces. However, every time I restart my computer, the hotcorner is forgotten. I have to turn it on and off in Unity Tweak Tool to make it work. Any solution?

---

### Post by smirnich on 2014-06-05
[COLOR=#000000]I run Ubuntu 14.04 on an HP Envy 6 Sleekbook with an AMD AMD A6-4455M APU with Radeon HD 7500G graphics.  Has anybody experienced the same or know what to do?[/COLOR]

---

### Post by mc4man on 2014-06-05
I haven't had such issues in quite some time, why?, don't know (maybe because I use rotate instead of wall.
Any way others have, one solution is to disable "Automatic plugin sorting" in ccsm > Preferences > Plugin list

Generally you also need to move some plugins to a lower position, see this thread for what monkeybrain20122 has settled on as he seems to be affected by this from time to time
[http://ubuntuforums.org/showthread.php?t=2224346](http://ubuntuforums.org/showthread.php?t=2224346) (post 3

Otherwise another solution would be to make the binding the default though that has a small downside in that the binding may be hard to disable if one decides to do (not hard to fix if so

---

### Post by monkeybrain20122 on 2014-06-05
This is an ongoing problem.

 Install CompizConfigSettingsManager (CCSM), check that "Expo" is activated and the hot corners are set. Then go to Preferences > Plugins list and disable auto plugin sorting (uncheck the box) and put "Expo" at the very bottom of the "enabled plugin"  list. Logout and login again.

The CCSM is kind of volatile, so use it with care. While you are moving Expo down the list you may experience momentary crashing of Unity, but it will come back if you wait a few seconds.

---

### Post by smirnich on 2014-06-09
Disabling automatic plug-in sorting and moving "expo" to the bottom solved my problem! Thank you :D

---

