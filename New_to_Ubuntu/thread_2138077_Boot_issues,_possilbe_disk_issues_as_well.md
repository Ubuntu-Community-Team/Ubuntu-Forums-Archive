---
title: "Boot issues, possilbe disk issues as well"
date: 2013-04-22
forum: New to Ubuntu
---

### Post by wings515 on 2013-04-22
Please excuse my complete ignorence, I had a lot of problems getting an HP Pavilion to install XP.  turns out there was a bug with SP3 and the AMD processor.  To make a long story short, a suggestion was to load ubuntu and format the drive to fix the MDR.  Well it fixed it alright, it went south.  So i downloaded Ubuntu 12.04.2 LTS.  It installed correctly (I think).  After restarting I get an error message 

HPthird login: [  23.590113]  [drm:drm_crtc_helper_set_config]  *ERROR*  failed to set mode on [CRTC:10]
[    23.710103] [drm:drm_crtc_helper_set_config *ERROR* failed to set mode on [CRTC:10]

Then it displays 
160 packages can be updated
81 updates are security updates

A bunch of Disclaimers
and then

dan@HPthird:~$


So what do I do now?


Thanks in advance.

Best regards,
wings515

---

### Post by cortman on 2013-04-22
Doesn't appear to have installed correctly. If you have nothing to lose, I would recommend reinstalling.
I am wondering what your goals are though, do you want to use Ubuntu just to wipe the HDD clean for a Windows reinstallation, or do you want to install and use Ubuntu permanently on that computer?

---

### Post by wings515 on 2013-04-22
Well I would like to learn ubuntu and use it permanently.  I just shut down the PC and restarted, it came back up without the CRTC errors but with the unix like prompt.

---

### Post by nonamedotc on 2013-04-22
Do you have discrete graphics card (Nvidia, ATI and such) installed in your system? I am asking because you mention a DRM error and you get a login prompt! It looks suspiciously like a display driver issue.

---

### Post by wings515 on 2013-04-22
No just the mother board video system.  The PC had at one time a GeForce 7600 but that is removed.

---

### Post by wings515 on 2013-04-22
When I did the install there were full graphics during the install with lots of pictures and a windows like wallpaper

---

### Post by wings515 on 2013-04-22
The last time I re-started a error message came up stating immenent disk failure.   Press f4 to continue.  Pressing f4 got me to the login screen

---

### Post by Impavidus on 2013-04-23
That warning of an imminent disk failure could explain something. When random parts of the disk are unreadable any error may happen. Can you boot (if necessary using the live disk you used for installing), go to disk utilities and check the SMART status of your drive? Maybe it's time to get a new drive.

---

### Post by wildmanne39 on 2013-04-23
Changed title to be more descriptive so you are more likely to get the help you need.

---

