---
title: "Zoom performance problem after upgrade 22.4 to 22.10"
date: 2023-03-06
forum: New to Ubuntu
---

### Post by geoffdraper on 2023-03-06
I have been running Ubuntu 22.04 for a year successfully, including attending Zoom meetings. 
Machine is Intel 64-bit with 8GB primary memory. 
I recently upgraded to Ubuntu 22.10. 
Zoom video now performs very badly:
- Other meeting participants appear as a series of still images about 1 second apart. Like slow-scan TV. 
- All their images update at the same moment. 
Joining calls is fine. Audio is fine. 
Any suggestion re how to fix this problem? 
- Is it a known Ubuntu 22.10 issue? Is it a configuration issue with Ubuntu or Zoom? Does 22.10 need more memory than 22.04? Or...?

---

### Post by kattrin on 2023-03-07
Try closing all programs or browser tabs that you do not use, as they can consume system resources and affect performance. 
If that doesn't help, try updating to the latest version of Zoom.

---

### Post by geoffdraper on 2023-03-07
Another problem I notice in Ubuntu 22.10 is that the game Klondike seems very slow and "spongy", compared to using it in 22.04.

---

### Post by monkeybrain20122 on 2023-03-08
If 22.04 was working well for you why did you upgrade to a release with only 9 month support? Besides, if you "upgrade" as oppose to a clean install something might have broken during "upgrade". In general the "upgrade" is more likely to succeed if there is less third party software (such as zoom) and less customization, but in which case there is less reason to "upgrade" instead of a clean install.

---

### Post by Impavidus on 2023-03-08
Memory requirements slowly go up over time, but 8GB should be more than enough. Could it be a graphics driver issue? Do you still have a kernel from 22.04 (they aren't autoremoved during the upgrade, but only after the first kernel upgrade on the new release)? If so, can you boot it and does that help?

22.04 with HWE moved to the same kernel as 22.10 recently, but with the GA kernel, that wouldn't happen.

---

### Post by ajgreeny on 2023-03-08
I haven't used Zoom since our UK lock downs, but how did you install it?

I always used the .deb version from the Zoom website but I see it is now available as a snap package.

---

### Post by ActionParsnip on 2023-03-08
If you make a fresh Ubuntu user then log in as that, is it OK there?

---

