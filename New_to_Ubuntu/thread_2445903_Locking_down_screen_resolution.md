---
title: "Locking down screen resolution?"
date: 2020-06-21
forum: New to Ubuntu
---

### Post by hunterjwizzard on 2020-06-21
Hi folks,

I'm very new to ubuntu but trying to make it work with my a very complex video toplogy. I currently have it hooked to two 4k monitors, but I am planning to run it at 1920x1080. Problem is if my switching equipment doesn't play right, it re-detects the screens and thus sets itself back to the monitor's native resolutions.

Now, I know from a hardware perspective why this is happening: None of my video switching equipment actually spoofs EDIDs properly. I'm solving that problem slowly but surely, but in the meantime I am wondering if I can trick/force Ubuntu to stop changing the resolution automagically?

EDIT: I should add its also auto-detecting settings when I reboot. So basically I can't currently leave it alone and expect to still be able to use it after.

---

### Post by Autodave on 2020-06-22
What video card, if any, do you have?  What drivers have you installed and where did you get them from?

---

### Post by hunterjwizzard on 2020-06-23
Geforce GTX 650, I believe I got the actual drivers from nVidia(and the card is just barely still supported). I have a 950 I may install.

The EDID problem will be solved in hardware(eventually: [http://monitordetectkiller.com/](http://monitordetectkiller.com/) the shipping is very slow), but the current issue is when I reboot it comes up and automatically picks the native resolution. I don't want it running at that resolution; I want it to run at the resolution I set it at the last time I had it running. It's also not saving the monitor configuration.

---

