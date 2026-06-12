---
title: "[SOLVED] Java Issue?"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by RussW210 on 2008-09-29
For some reason, when I visit sites like MLB.com and Xbox.com, the menu bars at the top get hidden behind java/flash when opened.  I have attached two desktop screenshots of it happening.  Does anyone have any idea?

---

### Post by RussW210 on 2008-09-29
Anybody?

---

### Post by RussW210 on 2008-09-29
bump

---

### Post by maruthi_s@infosys.com on 2008-09-29
[COLOR="Blue"]
Hi 

This is not the problem with the Java version, but the flash library that comes with Ubuntu. 

The latest patch for the flash library should resolve this issue. 

I got the below info from the Bug database. You can try this. 
Fix for Ubuntu Hardy (more complicated)

Fixing this bug in Hardy is not quite so straightforward.

Flash 9 is not compatible with PulseAudio unless libflashsupport is installed - however, libflashsupport causes crashes - see bug #192888.

Flash 10 is compatible with PulseAudio (but libflashsupport must be removed, as it still causes crashes). However, there are more pre-requisites to ensure it works correctly, including:

   1. To ensure all the fixes that are required for Intrepid (listed above) are applied to Hardy.
   2.

      Updates are released for alsa-lib and alsa-plugins: Hardy's version of the PulseAudio ALSA plugins do not function correctly, which is tracked in bug #192888.
   3.

      There needs to be a backport of alsa-lib that introduces an important change to the behaviour of PulseAudio, where the default ALSA device is set to PulseAudio. This has the potential to cause regressions in several applications, however. See bug #198453. 

Therefore, Hardy will require SRUs (StableReleaseUpgrades) on several packages, which could take some times - but most of all, needs proper testing in Intrepid before this can happen.

Please see my threads on Ubuntu Forums for the PulseAudio guides, as many of these issues are discussed:

    *

      For Hardy: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

      For Intrepid: [http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965)

Let me know whether it helped you. 
[/COLOR]

---

### Post by RussW210 on 2008-09-29
Great thanks, looking at them now...

---

### Post by RussW210 on 2008-09-29
Question: is nspluginwrapper the same as ndiswrapper?  I don't seem to have a nspluginwrapper in my Synaptic Package Manager.

---

### Post by RussW210 on 2008-09-29
Can't thank you enough [email]maruthi_s@infosys.com[/email]...

been looking for a solution to this problem for a while now and that Hardy guide you provided fixed it.  Much thanks!

---

