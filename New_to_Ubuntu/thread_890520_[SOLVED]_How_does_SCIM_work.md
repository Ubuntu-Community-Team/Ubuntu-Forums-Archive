---
title: "[SOLVED] How does SCIM work?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by zzzonked on 2008-08-15
I can't get SCIM to do anything. How do I even use it? I want to type Vietnamese/Hindi/Chinese but none of the toggle shortcut keys work and I can't find any button that says toggle.

Figured it out after a very intensive toying around session :p

---

### Post by Popaul on 2008-09-12
Hi! I still have problem to get SCIM start to be useful... Nothing happens. Could you explained what you did?
Thank you!

---

### Post by Popaul on 2008-09-12
:)Fixed, but the hard way. Probably some file was corrupted in the end.
So, what I did:

system: Ubuntu Hardy Heron 8.04 up-to-date
Started Synaptic through menu system/Administration/Synaptic Package Manager
Search for "scim"
All file with 'scim' in their name: marked them for Complete Removal (I guess if just 'removal', some files will be left on the system and will be used again during the next install, so problem).
Some files are automatically marked for removal once you mark 'scim' for example. I made sure that all these are really marked for Complete Removal.
That removes all the language support files (files starting with language...).
CTRL+Alt+Bckspce to log out and log-in so that the changes get some effects.
Then I went to menu System/Administration/Language Support
I ticked the languages I wanted to add. The system then re-installed automatically all the files needed. Oooops... as I wanted Japanese and Chinese (I suppose that is valid also for Thai, Vietnamese or some others languages like these): I checked the box Input method: Enable support to enter complex characters. And of course I verified that the Default Language was the correct one, i.e. my locale.
But it installs only SCIM alone, which is not good enough for Hardy.
So back to Synaptic, search for 'scim' and select for installation all the 4 scim-bridge-... files (agent, gtk...), as Hardy needs the bridges to use SCIM.
Re log-out and log-in, and... the little applet liek a keyboard was up there. Right-click to open the SCIM setup, menu 'GTK' to select 'Toolbar/Show' "Always" (or "On Demand"... up to you) and a little square with "SCIM" on it appear magically in the lower right corner of the screen. And... OOWriter opened, did ctrl+space and the SCIM toolbar opened: I could select any of the languages I've checked in Language Support and it works. Paradise.

---

