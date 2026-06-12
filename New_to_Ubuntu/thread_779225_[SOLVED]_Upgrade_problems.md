---
title: "[SOLVED] Upgrade problems"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Michael Dooley on 2008-05-02
I have beeen running Gutsy for about five weeks. I have loaded and run dosemu and virtualbox (as well as other web apps) and things seemed to be going well. However, my modem and my video card both use restricted drivers. (Radeon 9550 AGP and Conexant modem.) I kept up with the various Gutsy upgrades. I attempted to upgrade to Hardy from the Alternative CD last night. Now my boot process fails.

At the end of the installation process this morning (the computer needed to download several files from the net during the night) I got the following messages in this order:

Sorry the package "xserver-xorg-video-chips" failed to install or upgrade.

Sorry the package "virtualbox-ose" failed to install or upgrade.

Sorry the package "update-manager" failed to install or upgrade.

Sorry the package "ubuntu-docs" failed to install or upgrade.

Sorry the package "libxmlz" failed to install or upgrade.

Sorry the package "xserver-xorg-core" failed to install or upgrade.

Sorry the package "xserver-xorg-video-savage" failed to install or upgrade.

Several of the failures to install returned messages similar to the following:

"subprocess dpkg split returned error exit status 2"

Could you please suggest what I can do in grub to get this situation rectified? And as a result of getting these errors, I suspect that the Alternative CD was somehow defective. 

My first thought was a reinstall via the live CD or perhaps the alternative CD but I have no experiance with this sort of thing.

Thank you for your time.

---

### Post by Michael Dooley on 2008-05-02
I will try to see if the Alternate CD rescue capability is of any use to me. I am hopeful that I can make some progress without resorting to a live CD re-install.

Before starting up in a terminal mode I did use the self test capability of the Alternate CD and it said that the CD's contents were good. We'll see.

I'll check back later and see if anyone here has some suggestions as to what to do to correct the various problems I listed above.

Thanks.

---

### Post by Michael Dooley on 2008-05-02
Problem solved.

The source of my difficulties finally turned out to be faulty CD media. Both the 8.04 live CD and the 8.04 Alternative CD were bad. I exchanged my CD burner for one in another machine and it could barely read the media. I copied both CDs on one of my Windows machines and saw that Nero was having a hard time (slow) verifying all the sectors (?). At any rate, after this back a**ward cleansing method, both CDs worked.

I'll talk with my buddy tomorrow and let him know that there may be a problem with his CD burning situation. He uses old machines too but since he writes code (pretty simple software demands) and is on a fast network, it doesn't particularly matter.

Except in this one instance.

---

