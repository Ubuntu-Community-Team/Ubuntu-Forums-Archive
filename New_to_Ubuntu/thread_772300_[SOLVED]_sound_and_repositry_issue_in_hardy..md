---
title: "[SOLVED] sound and repositry issue in hardy."
date: 2008-04-28
forum: New to Ubuntu
---

### Post by bhadotia on 2008-04-28
[LEFT]I upgraded my ubuntu few days back. Although outward feel of hardy is impressive but there are a few problems which I am facing . First of all the sound is too loud and harsh , I have read a few posts in the forum with the same problem so I don't think I need to explain .  
The sound was fine after the first restart after the upgrade, but now this problem is showing up.


One more thing, what should be done with the old repositries of 7.10 in the software sources; should I enable , disable or delete them. And will I have to add medibuntu and launchpad repositries for hardy seperately? I don't think that they were upgraded with the distro upgrade.
[/LEFT]

---

### Post by TerpInHotLanta on 2008-04-28
I believe you will need to update the medibuntu and launchpad repos yourself (at least it didn't update any of my user-added repos when I upgraded several weeks ago).

I would keep the 7.10 repos around if they're there-- I don't think it matters, as your hardy installs will eventually replace all your 7.10 installs.

I don't have an answer on the sound issue for you. I know some System76 people and others have had the sound issues and manufacturer-released drivers fixed the problem. I haven't had any problems with sound fidelity-- wish I could be of more help.

-'Luck
Charlie

---

### Post by forrestcupp on 2008-04-28
Well, your sound problem is because they switched to Pulse Audio.  You could switch it all back to Alsa and maybe that would help.  Go to System->Preferences->Sound and in the Devices tab set all of the drop down boxes to ALSA.  If you ever want to, you can change it back to 'Autodetect'.

I don't know if you have to reboot or not.

As for your 3rd Party Gutsy repos, I'd check with the individual repos to see if they have a Hardy repo now, instead.  Most of them do.  It's best not to mix Hardy and Gutsy repos because they depend on different versions of things.

---

### Post by bhadotia on 2008-04-29
I switched everything back to alsa but when I tried to test the devices the following message came :

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.


What does it mean? I have not restarted my computer yet to see if it is working coz I'm downloading some packages throug synaptics(big packages).

---

### Post by bhadotia on 2008-04-30
After the restart there was no improvement in the sound quality with ALSA also. I have switched back to autodetect. Any other suggestions?

---

### Post by bhadotia on 2008-06-04
Thanx, I have got the sound problem fixed. Look [http://ubuntuforums.org/showthread.php?t=782858](http://ubuntuforums.org/showthread.php?t=782858)_._

---

