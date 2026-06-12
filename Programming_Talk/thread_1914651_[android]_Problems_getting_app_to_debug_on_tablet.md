---
title: "[android] Problems getting app to debug on tablet"
date: 2012-01-24
forum: Programming Talk
---

### Post by KdotJ on 2012-01-24
Hey all, hopefully some Android guru will be able to help me out.

I'm currently developing an application, and there no problems when I install it onto my phone for debugging and testing (I'm doing it via eclipse). It installs fine and I can run it as intended. 

However, when I try to install it onto my tablet to test it, it installs fine according to the output in eclipse "Success!" but when I try to launch the app from the tablet, nothing happens. It won't open at all.

Now my phone is running Gingerbread (at API level 10) and my tablet is running Honeycomb (at API level 11). In my Manifest, the uses-sdk attribute is set for 10 to minimum (which also means the target is set to 10 by default). I've tried changing the target to 11 but still no joy.

Any ideas?

Thanks in advance!

---

### Post by lykeion on 2012-01-29
Try to change the project target to android-11 in the default.properties file in the project folder, restart eclipse and deploy it to your tablet.

---

### Post by KdotJ on 2012-01-29
Thanks for the reply, I'll give this go. As of so far I've only changed it in the manifest, so I'll try the properties.

---

