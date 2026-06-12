---
title: "Ubuntu 11.10 Gnome Classic Desktop Not Fully Loading"
date: 2012-01-24
forum: New to Ubuntu
---

### Post by codyallensmith on 2012-01-24
Hi,

I have Ubuntu 11.10 and it comes with Unity but I hated it with a passion so I uninstalled that and installed Gnome Classic. That did not cause any problems for me. 

But eventually my second monitor wasn't being noticed so i ran "nvidia-settings" since i have an nvidia gpu and from there i enabled my second monitor. it said it can't save settings and that i have to save to x config file and then restart x. so i tried doing that but did not check the box to merge into existing x config file. and when i hit save and restarted my pc, it didn't work.

this next time i did the same thing but checked the box to merge into existing x config file. it kind of worked. it made both my monitors open up. but i couldn't bring anything to the left monitor. i like separate monitors that act as one big monitor.

then i noticed a checkbox under nvidia-settings that said to enable xinerama and i enabled that thinking that would fix my problems. i checked the box to overwrite my x config file and saved and restarted my pc.

this time is when problems started happening. it brings up the login screen alright. when i enter my password, it loads the desktop background, but that is it. it doens't load any desktop icons. i can NOT go to the top left corner to open up the cool view mode where i can see all my applications and shortcuts. hitting ctrl alt t does not bring up terminal. there is no taskbar anywhere on my screen. there is no start/shutdown button, nothing. 

my mouse  cursor does work and i can create new folder, create new blank document, and change desktop background. when i click change desktop background i can then click the button "all settings" to go to system settings. this is the best i can do. i have no clue how to get to terminal. very frustrating..

---

### Post by GraeW on 2012-01-25
I wish I had an answer for you - I know when I did an install of 11.04 on my desktop last Spring everything seemed to pop up ok once I did the Nvidia stuff you did above. Anyone else out there have an answer short of removing and reinstalling the X packages?

---

