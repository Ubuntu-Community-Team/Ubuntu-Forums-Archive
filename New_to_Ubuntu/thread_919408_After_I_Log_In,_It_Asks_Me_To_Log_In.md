---
title: "After I Log In, It Asks Me To Log In"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by blobdole on 2008-09-13
So I just installed 8.04 on a friend's computer and have come across an issue I haven't seen before.

The log in screen appears.
I log in successfully.
The log in screen goes away.
The sound plays.
The sound cuts out near the end of the sound.
The monitor says it has entered sleep mode.
The log in screen appears.
Repeat.

Whaaa?

---

### Post by kansasnoob on 2008-09-14
I never have either:confused:

Free bump:(

---

### Post by JillSwift on 2008-09-14
It sounds like Xorg is crashing.

Video card, video memory size, monitor, memory, cpu?

---

### Post by lisati on 2008-09-14
I had something similar happen when I checked out 8.04 on both my machines, which is why I've stuck with 7.04 for now. The suggestion that there could be a problem with xorg configuration rings true - I think there are other threads on the forum which deal with this, but the links elude me for the moment.

---

### Post by R_T_H on 2008-09-14
Log in in the safe session mode and look at xorg as people have suggested. Can't really add any more than that, I'm afraid :(

---

### Post by markbuntu on 2008-09-14
There are a number of reasons why this could happen but, you should be able to login in a gnome safe mode session and look in the logs. At the login screen there is a little icon on the bottom left that you can change session from. You can look in the logs by going to System/Administration/System Log.

In the Xorg.0.log look for lines that start with (EE).
In the syslog or kernel log look for references to a missing file in (gdm) lines.

You can also just try making a new user and password. That sometimes works.

---

