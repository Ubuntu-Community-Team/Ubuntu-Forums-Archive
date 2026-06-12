---
title: "Oracle VM VirtualBox running Ubuntu 14.04"
date: 2014-04-22
forum: New to Ubuntu
---

### Post by johnu1960 on 2014-04-22
Hi.

I had been running Ubuntu 13.1 in an Oracle VM VirtualBox without problems.  During a recent upgrade I was prompted to upgrade Ubuntu to 14.04 so I decided to give it a try.  It took many MANY hours to install the upgrade and when it did, it used a different video driver.  When I select About this Computer, it indicates that the graphics is Gallium 0.4 on llvmpipe.  As I recall from the previous (13.1) install, the video system was running something specific to Oracle VM (I don't recall the name).  The problem at present is that the only resolution possible is 640x480.  The desktop will not fit into the box provided by the VM so the system is not usable.  The icons show up as extremely large and applications can only show part of their screens.   

Can anyone tell me how to install a video driver that will work on Ubuntu 14.04 under the Oracle VM?  Thanks very much.

---

### Post by SeijiSensei on 2014-04-23
Do you have the Extension Pack installed?  It can help with video problems.

---

### Post by jdeca57 on 2014-04-23
I updated this Oracle Virtualbox machine from 13.10 to 14.04 with little or no problems. After the update I only installed the guest additions but since I did that in 13.10 the kernel headers were already included and in could simply install the additions. Perhaps it's also a question of Video memory, a setting you can select in Virtualbox. I chose 128 MB (the max) and 3D, but of course you won't get 3D. I'd look into those two things (Graphic memory and Guest Additions) first.

---

