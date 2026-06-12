---
title: "HOWTO: Fix System Sounds when program sounds work correctly"
date: 2005-04-18
forum: Outdated Tutorials &amp; Tips
---

### Post by connellr on 2005-04-18
This fix is painfully simple, but has worked for me several times, I hope it helps some of you having this problem too:

i) If you cant hear sounds in other programs (ie: media players, video, etc) then this is not the howto for you ... there are many other posts on how to get sounds in programs working, this post is how to get system (event) sounds to work when the other sounds work.

ii) This is tested using ALSA for all of your sound server settings ... if you havent rebooted since choosing ALSA for your sound server run 'sudo killall esd' before proceeding. (You can choose ALSA as your sound server in System > Preferences >  Multimedia Sysem Selector - Set both Sync and Source to ALSA).

1) Click on System > Preferences > Sound
2) Uncheck "Enable Sound Server Startup"
3) Log out of Gnome
4) Log back into Gnome
5) Go back to System > Preferences > Sound
6) Check "Enable Sound Server Startup"
7) Test, if all went well your system sounds should now work.

It appears that although the 'sound server startup' option is checked, it isn't really enabled.  The above has fixed the problem for me numerous times.

---

### Post by connellr on 2005-04-18
The same fix appears to work in KDE (kubuntu) as well:

1) Goto System > Settings
2) Click on 'Sound & Multimedia'
3) Click on 'System Notifications'
4) Click on 'Player Settings' Button
5) Select 'Use External Player' and type 'aplay' in the box.
6) Click 'OK' for both screens
7) Test it this way (my experiance is that sounds are choppy this way and get cut off)
8) If you heard sounds at step 7 continue on to the following steps
9) Repeat steps 3-4
10) Choose 'Use the KDE Sound System'
11) Click OK twice and test (At this point all sounds worked correctly for me in KDE)

Let me know if these instructions helped.

---

### Post by Jubalgunn on 2006-11-10
This is no longer applicable in Edgy.
The options for enabling the sound server have gone. :(

---

