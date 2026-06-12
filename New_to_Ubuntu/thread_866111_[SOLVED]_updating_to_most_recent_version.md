---
title: "[SOLVED] updating to most recent version"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by DarchAengel on 2008-07-21
Hi all, I just updated to Hardy heron after not having internet for the a few months.  I thought it was the most recent version there was (8.04) but there seems to be one after it(8.04.1).  Is there a way that I can upgrade to this without having to burn an ISO since I do not have access to a functional burner at the moment.  This is an issue since I have lost sound with this upgrade and am hoping going one higher will making fixing that issue that much simpler.

---

### Post by ibutho on 2008-07-21
If you installed 8.04 and update your system using the package manager, then you already have 8.04.1. 8.04.1 is just a point release and you do not need new media or to do a dist-upgrade to get it.

---

### Post by appi2012 on 2008-07-21
Do you have internet now? If so, update manager should have already updated you to 8.04.1 (8.04.1 just has updated packages) Update manager won't say there's a new release out because there isn't, it is just a iso of more recent packages.

---

### Post by drs305 on 2008-07-21
```
lsb_release -a
```

This is what you will see if it's the latest:
```
Ubuntu 8.04.1
```

---

### Post by DarchAengel on 2008-07-21
Thanks everyone for the help so far.  When I typed in the code it told me I have Ubuntu 8.04.  Would there be a way to fix my sound issue without having to try and upgrade since a lot of you said that there isn't that much a of a difference between the two.  The issue is that, like I said, the sound suddenly stopped working with the upgrade.  Be it Movie Player, Rhythymbox, or anything I use it comes up with an invalid argument and can't connect to stream.  How do I go about pinpointing the problem.  Thanks again.

---

### Post by drs305 on 2008-07-21
One of the most common sound fixes after an update is to go to System, Preferences, Sound and change the preferences in the Devices tab back to ALSA if they have been changed to PulseAudio.

Added: Use the 'test' button to see if the sound is restored. If it isn't, you might try another mode.

---

### Post by DarchAengel on 2008-07-21
I checked the sound preferences and everything is set to ALSA.  That doesn't seem to be the problem.

---

### Post by DarchAengel on 2008-07-21
Thanks guys again.  We got it to work.  It seems we needed to reinstall the drivers again.

---

