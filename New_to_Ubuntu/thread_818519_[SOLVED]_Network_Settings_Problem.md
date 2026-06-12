---
title: "[SOLVED] Network Settings Problem"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by oronte on 2008-06-04
I've just installed Ubuntu 8 64bit edition on a brand new PC. I used the network settings on the top panel to set up my phone (which is connected via USB). First I set it up as GPRS/UMTS but it didn't work. I set it up as Serial and it worked for a brief second (registered on my phone) but then it returned to the GPRS settings. Now, no matter what I change the settings to, once I accept them it automatically returns to the GPRS setting. How do I 'clear' it?

---

### Post by jbrown96 on 2008-06-07
Not sure about cellular modems but wireless there are two ways that I know of. Right clicking on network-manager icon and edit wireless networks. The configuration might be in there. 
The other way, I think, is more promising. In your home folder, press Crtl+H to show hidden folders. Navigate to .gconf-->System-->networking and browse around till you can find the correct folder. Simply delete the parent folder and the configuration should be deleted.

---

