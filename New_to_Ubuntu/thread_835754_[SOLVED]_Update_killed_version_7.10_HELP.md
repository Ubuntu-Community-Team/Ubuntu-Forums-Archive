---
title: "[SOLVED] Update killed version 7.10 HELP"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by comsparks on 2008-06-20
I noticed that there were updates today so I updated like I always do. The computer was slow rebooting and I got the boot screen but I now have a black screen with a white cursor blinking on it. I can't seem to enter anything. Any one have any ideas as to how to fix this problem. Thanks

Problem is fixed. I finally found some help about this problem. What I did was during grub (boot) startup I pressed the Esc key, chose the restore option for core 15 and logged in as root. I then typed in envy -t and uninstall Nvidia drivers. I then reinstalled the Nvidia drivers from the envy menu and then allowed the xorg to be updated. I then rebooted and all came up great.

---

