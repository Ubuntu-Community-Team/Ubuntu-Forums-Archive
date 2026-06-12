---
title: "Ubuntu 18.04 LTS hangs (need to hold power button 4 sec to power off PC)"
date: 2019-04-18
forum: New to Ubuntu
---

### Post by volandsz on 2019-04-18
Hi i am new to linux (but not to PC ecosystem) and having some stange issues with my new Ubuntu 18.04 installed.
My PC is just some regular chineese small form factor Celereon J1900 with 8gb of ram and 128gb mSata SSD
It was working ok under windows 7 but kinda slow and i decided to switch to linux -> Ubuntu to learn and maybe gain some performance.
Installation went smoothly but then some strange things startet to happen:
PC can be ok literally for days with just user desktop active, but if i run for example browser (firefox preinstalled), just open 
browser window no site opened or anything PC will hang (4sec power button reset only) same goes for Remmina VNC client
As far as i can tell temps are around 40C it is ok for passively cooled PC. I can not test memory because this option is not available on
 UEFI boot (and i dont have option in BIOS to switch to non UEFI on this PC) but i tested memory when Windows was installed and it was ok (1 week before)
Can you help me please? Maybe there are some system logs that i can check? Or any other options?
If possible give answer with example (ie. terminal command) because i am still new to linux.
Thank you very much

---

### Post by crip720 on 2019-04-18
It seems to be intel's c-state bug.  I don't know enough to give instruction or link here, but you just have to to google 'ubuntu c-state bug'.  Easy to fix, but different kernels and hardware configurations will give different outcomes from very good to poor.  This from my own problems with this from ubuntu 15.04, most been good except for 15.10.

---

### Post by volandsz on 2019-04-19
Looks like it was it. I tried two things:
1. [https://askubuntu.com/questions/749349/how-to-set-intel-idle-max-cstate-1](https://askubuntu.com/questions/749349/how-to-set-intel-idle-max-cstate-1)
2. [https://bugzilla.kernel.org/attachment.cgi?id=223851](https://bugzilla.kernel.org/attachment.cgi?id=223851)
Not sure what helped but in the end - 6 hours with browser opened and system seems stable. I dont understand why so obvious and important for stability feature not implemented by deafult. :(
Thank you very much crip720!!!!

---

