---
title: "Mic Not working properly"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by JCDenton1o1 on 2008-06-05
When ever I try to use VOIP programs like skype, my friends on the other side cant here me, unless I scream at the top of my lungs, and even then its too faint. I turned on the mic boost, and set all the sound bars to max, but that doesn't seem to do anything. Whenever I go into sound recorder to test, it just keeps telling me my multimedia settings are wrong, but give no hint to whats wrong.

help!

---

### Post by michaelaly on 2008-06-05
Try the mic on a another computer/OS if possible. I had a similar problem and it turned out the mic hardware was faulty. 
Question, is the mic USB or standard 1/4"?

---

### Post by ubuntu-freak on 2008-06-05
Is Hardy your first taste of Ubuntu? It uses a new sound server called PulseAudio, so you may have better results (for now) using the sound server that was previously default:
 
**sudo apt-get install esound** 

That should remove the PulseAudio sound server also. You may need to go into the preferences of non-GNOME apps (such as VLC, MPlayer etc) and switch the sound driver to ALSA.
 
Reboot/logout as well.

---

### Post by JCDenton1o1 on 2008-06-05
michaelaly: No, just this one, and its a 1/4 plug

RO: all right all see what that does.

---

### Post by ubuntu-freak on 2008-06-05
It would actually be ideal if you could test another mic.

---

### Post by JCDenton1o1 on 2008-06-05
I dont have another mic unfortently, but the switching of the sound program has left me with no sound at all.

---

### Post by JCDenton1o1 on 2008-06-05
im done, nothing is working on my computer now, im going back to windows. Bye.

---

### Post by ubuntu-freak on 2008-06-05
> **JCDenton1o1 said:**
> im done, nothing is working on my computer now, im going back to windows. Bye.

 
Why? Navigate to System > Preferences > Sound and select ALSA, instead of Autodetect. Also, you can remove Esound and reinstall the PulseAudio-related packages if you still have issues with Esound. We don't even know if it was perhaps your mic causing the trouble in the first place.

---

