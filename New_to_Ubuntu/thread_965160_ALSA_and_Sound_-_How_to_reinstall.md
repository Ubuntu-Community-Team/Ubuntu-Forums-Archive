---
title: "ALSA and Sound - How to reinstall?"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by YaSoC on 2008-10-31
Hey!

I've updated my Ubuntu to 8.10 yesterday and it works fine... But then i've met some problems with my Sound. (at least in Skype, it couldnt init. sound devices by default, and when i choosed "hda_intel, 0" or something like this - just only left speaker worked)

So i decided to solve this problem. The first i've tried was compiling ALSA from sources, i've seen there were some errors, but decided to install it anyway. Now there is no sound in my system and i've tried to uninstall all of ALSA packages, reinstall, completely removed em with Synaptic etc... nothing helps me.

I think there are almost some troubles and maybe errors in my drivers and configuration files.


How can I completely uninstall all this ALSA and/or anything else i need, then to install everything cleanly with re-downloaded packages from internet?

---

### Post by ethoxyethaan on 2008-10-31
Skype and gstreamer conflict sometimes,
i think there was no problem with ALSA by default though. 
sudo apt-get autoremove alsa to remove it.

---

### Post by YaSoC on 2008-10-31
> **ethoxyethaan said:**
> Skype and gstreamer conflict sometimes,
i think there was no problem with ALSA by default though. 
sudo apt-get autoremove alsa to remove it.

The second problem was, that the mixer didnt remember my options and on every boot i was in need to re-configure it (such as turn microphone sound off etc)
Third - playing music caused my speakers to have overflows, so the sound wasn't clean. 

Just tried ur solution... 
it removed several packages, just one i've seen with "alsa" was alsa-base

now i'll reboot and try to install alsa again.

---

### Post by YaSoC on 2008-10-31
Doesn't work.



Double clickin' mixer's icon at the top panel shows error message

(translated) "GStreamer modules and/or devices to change volume power are not presented."

also the same, but in Russian:

"The volume control did not find any elements and/or devices to control.
This means either that you don't have the right GStreamer plugins installed,
or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the
speaker icon on the panel and selecting "Remove From Panel" from the menu."

---

