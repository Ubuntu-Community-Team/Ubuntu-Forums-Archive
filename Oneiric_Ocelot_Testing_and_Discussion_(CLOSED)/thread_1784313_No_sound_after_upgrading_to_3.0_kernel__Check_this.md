---
title: "No sound after upgrading to 3.0 kernel?  Check this."
date: 2011-06-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by 3vi1 on 2011-06-16
After upgrading to the 3.0 kernel, I no longer had sound out of my main speakers, just my headphones.  This is with the HDA Intel chipset.

Looking in alsamixer, there appears to be a new "Auto-Mute Mode" and it was set to enabled.  Disabling it in alsamixer fixed the problem.

I just thought I would mention it here in case someone searches on the symptoms, because I'd think that's a pretty common chipset and the auto-mute mode setting does not appear in the normal sound preferences GUI dialogs.

Carry on with the testing!  :)

---

### Post by seeker5528 on 2011-06-16
> **3vi1 said:**
> After upgrading to the 3.0 kernel, I no longer had sound out of my main speakers, just my headphones.  This is with the HDA Intel chipset.

Looking in alsamixer, there appears to be a new "Auto-Mute Mode" and it was set to enabled.  Disabling it in alsamixer fixed the problem.

I started seeing something like that with my stuff, but my headphones plug in to a jack on the volume control doohickey that goes to my speakers so the volume control can be used with the headphones and I wouldn't think that kind of status information could be sent back to the system, so I expect my only solution is to unplug my headphones. :(

Does seem like something that started pretty recently though, somewhere between one to two weeks since I noticed it to one month prior to that, give or take two weeks, since the last time I listened to something through the speakers. 

Later, Seeker

---

### Post by cariboo on 2011-06-17
I had a problem that nothing to do with auto-mute. When I went to Sound Preferences->Hardware, and clicked the Test Speaker button, the sound would work, but I couldn't get sound anywhere else, clicking on the Output tab I found that HDMI was selected. Once I changed it to Internal Analog sound, I had sound everywhere again.

---

