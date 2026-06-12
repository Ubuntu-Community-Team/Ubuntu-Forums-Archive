---
title: "[SOLVED] 7.10 to 8.04 upgrade had errors, hung, now what?"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by anewguy on 2008-04-25
My upgrade tonight from 7.10 to 8.04 had a problem with network-manager and then with network-manager-gnome.  Went ALMOST to the end of the progress bar, then just hung.  This means if there was anything after the place it hung that needed to be installed, it was lost.  In addition, since it hung in the installation phase it never went to the clean up phase.  So, how do I figure out what the status of my system is, what might be missing, and how to finish the installation and clean up?

When the system hung, I pressed the reset button and my PC rebooted and loaded into 8.04.  The first boot a came up with a crash of network manager and had me go through the reporting of a bug process, but I never made it all the way through that so no bug was reported.  Obviously I still have my wireless network connection, so I guess I must be running off an "old" network-manager.

I'm afraid to attempt anything as I don't know if my system is stable.:confused:

---

### Post by Saya on 2008-04-25
Try sudo dpkg --configure -a in a xterm session.

---

### Post by anewguy on 2008-04-25
> **Saya said:**
> Try sudo dpkg --configure -a in a xterm session.

Thanks!  That seemed to take care of the network-manager and network-manager-gnome problems.  I ran the system update procedure and clicked "check", and it thinks I don't need anything, so I'm guessing it was at the end of the installation phase.  Now I just need to know what the clean up phase does and how to do it.

Thanks! :)

---

### Post by Saya on 2008-04-25
> **anewguy said:**
> Now I just need to know what the clean up phase does and how to do it.
Open Synaptic, pick the Status tab and then Installed (local or obsolete). There'll be some redundant stuff. (can't guarantee that applies to everything, check every entry)

---

