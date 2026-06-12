---
title: "ATI Proprietary Drivers (X1200) and Suspend on UBUNTU 8.10"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by miltonlaufer on 2008-11-02
I just upgraded to 8.10, and everything was great, but now I can't resume after suspending. I tried disabling the ATI/AMD proprietary drivers and it works, but I really need to have 3D acceleration. So, I turned on again the propietary drivers... but also I need to suspend my laptop.

How should I do next?

---

### Post by PmDematagoda on 2008-11-02
According to some sources(and the fglrx package in Intrepid), it would seem that the fglrx driver currently in Ubuntu 8.10 is a beta and not a final release, so that may be the problem here. Another thing is that ATi has been a bit slow on supporting Xorg 1.5 and above(I believe the version in Intrepid is 1.5.1 or 1.5.2), so this may be another reason for broken support which may take some time to return.

---

