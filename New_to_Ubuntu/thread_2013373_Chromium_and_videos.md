---
title: "Chromium and videos"
date: 2012-06-30
forum: New to Ubuntu
---

### Post by ericstrom on 2012-06-30
Using Ubuntu Lucid Lynx

Moved from Google Chrome to Chromium today because Chrome was no longer opening. I did this through the Software Center. Things seems to go fine but now I'm noticing I can't view most videos; even on youtube. Looks like a plugin problem but not sure which one I need.

What do I do to get videos working again ?

---

### Post by ron999 on 2012-06-30
> **ericstrom said:**
> ...What do I do to get videos working again ?
Hi
Check that these 4 packages are installed:-
chromium-browser
chromium-codecs-ffmpeg-extra
chromium-browser-l10n
flashplugin-installer

---

### Post by mapes12 on 2012-06-30
I would completely uninstall both browsers. Synaptic does this better than Software Centre IMO. Then re install Chromium. To make sure you have all the codecs:-

- Install ubuntu-restricted-extras
- Go to the medibuntu website and follow the instructions to load up the codecs
- Install the VLC media player just for good measure

---

### Post by lovinglinux on 2012-06-30
The new version of Chrome comes with the new PepperFlash plugin. Unfortunately, this seems to cause the startup issue. See [http://ubuntuforums.org/showthread.php?t=2011882](http://ubuntuforums.org/showthread.php?t=2011882) for possible solutions.

---

### Post by ericstrom on 2012-06-30
How do I check that the 4 packages you specified are loaded ?

---

