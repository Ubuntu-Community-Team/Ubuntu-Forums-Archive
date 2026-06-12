---
title: "ubuntu precise boot process is always looking for wired network"
date: 2012-10-08
forum: New to Ubuntu
---

### Post by herbert tamayo on 2012-10-08
Hi, after install ubuntu precise pangolin, each time I start my pc it always looking for wired network connection, so if there is no cabled plug to my eth0 the boot process delays up to 4 minutes, so my question is: how can I deactivate the looking for a wired network connection?

regards

---

### Post by Bucky Ball on 2012-10-08
Right click Network icon>Edi Connections>edit Wired connection>IPv4 tab>Make sure 'Connect Automatically' is not checked.

Any luck?

---

### Post by shenmeister on 2013-03-08
I know this thread is pretty old and I'm not the OP, but I just wanted to say that the proposed solution solved my problem. After installing 12.04, it would constantly look for a wired connection and it would always indicate that wired connection is disconnected. Seems silly to be automatically looking for a wired connection when no ethernet cable is plugged in.

I found that the "Connect Automatically" checkbox was located directly in the "Editing Wired Connection" dialog box and not on any particular tab.

---

### Post by Absolute Terror on 2013-03-08
This happened to me with a Belkin USB adaptor.

I ended up just buying a new card for it. Panda Wireless makes ones that natively support Ubuntu but the range sucks.

---

