---
title: "no refresh rate &amp; not able to set folder perm.."
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Snappo on 2008-05-31
Hi, i have no refresh rate and it won't let me set it higher than zero. I'm using a packard bell easynote r1. Also, i'm not able to move files to my xamp folder and when  i try to set as share it says the permissions can not be set.

---

### Post by Snappo on 2008-06-02
oi & bump

---

### Post by SunnyRabbiera on 2008-06-02
what is your version of ubuntu?

---

### Post by Snappo on 2008-06-02
I've reinstalled ubuntu and now it uses a versa driver and i'm not able to edit the current post so the new thread is [http://ubuntuforums.org/showthread.php?t=816654](http://ubuntuforums.org/showthread.php?t=816654)

---

### Post by SunnyRabbiera on 2008-06-02
alright, and you already posted your specs in the other topic:

> 00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 02)

first I suggest trying to edit your monitor settings by going into a terminal and typing in gksu displayconfig-gtk
this will allow you to edit your monitor and video card settings.
Your via card should not give you many issues as via is usally good with linux support, you can see if its picked up in the graphics card tab.
in the screen tab, you may wish to play around with the monitor, even if your monitor is not picked up you can use one of the generic monitor settings.
thats how I fixed my issue, I have a HP pavilion MX50 monitor that is picked up as a plug and play, but I could not get resolutions above 800x600.
what I had to do is use another generic monitor setting and it works at my max resulution of 1024x768

---

### Post by Snappo on 2008-06-03
> **SunnyRabbiera said:**
> alright, and you already posted your specs in the other topic:



first I suggest trying to edit your monitor settings by going into a terminal and typing in gksu displayconfig-gtk
this will allow you to edit your monitor and video card settings.
Your via card should not give you many issues as via is usally good with linux support, you can see if its picked up in the graphics card tab.
in the screen tab, you may wish to play around with the monitor, even if your monitor is not picked up you can use one of the generic monitor settings.
thats how I fixed my issue, I have a HP pavilion MX50 monitor that is picked up as a plug and play, but I could not get resolutions above 800x600.
what I had to do is use another generic monitor setting and it works at my max resulution of 1024x768


I've had a wee mess around testing the lcd screen panel settings etc and no luck. As for my x file it doesn't show anything about resolution or refresh rate and i even tried to create a section in there to test but nothing.

---

### Post by Snappo on 2008-06-03
I fixed it by myself! :D:D:D!!!!!!:D:D:D!!

---

