---
title: "HELP! Various issues, Ubuntu freezes."
date: 2008-11-17
forum: New to Ubuntu
---

### Post by broken sword on 2008-11-17
I've done a clean install of 8.10.  And I've had a lot of issues. They might all be related.  Here are my specs:

Dell M1530, 4GB RAM, 200GB HD, 2.6 Ghz processor.
Two partitions: 30GB ext2, 170GB ntfs
And I have an Nvidia card
I've installed the medibuntu package, wine and a few other apps.

1) Programs keep freezing (window turns gray). Sometimes it's firefox, sometimes it's OpenOffice, sometimes, the terminal.  But mainly it's the Panel.  (as of right now, the panel is frozen and I can't click any menu options.  When this happens, I have to restart.  I can't access the Session manager to see if there are any issues.  And I'm not well versed with Linux commands, so I'm at a loss on how to troubleshoot.

2) VMware freezes, but only when I try to run a guest OS (XP Pro).  I can start it w/o a problem, but I try to run a guest OS it freezes.  And if I want to start it again I have to restart.

3) When I install some programs, the Menu entries aren't created automatically.  This would be ok for me in windows, but I'm clueless in Linux. Is there any way to fix this?

4) When using Terminal Server to connect to Windows servers, sometimes the program disables the mouse.  And I have to use the keyboard to get anything done. How can I avoid this? I need to be able to do this for my job.

Any help would be greatly appreciated

---

### Post by Keen101 on 2008-11-17
is compiz running?   If compiz is running it might be the problem for the programs freezing. Either that or your current video driver is not working correctly. 

>System >Prefrences >Appearance to disable compiz.

>System >Administration >Hardware Drivers to enable/disable proprietary Nvidia drivers.

---

### Post by handydan918 on 2008-11-17
> **Keen101 said:**
> is compiz running?   If compiz is running it might be the problem for the programs freezing. Either that or your current video driver is not working correctly. 

>System >Prefrences >Appearance to disable compiz.

>System >Administration >Hardware Drivers to enable/disable proprietary Nvidia drivers.

+1 on the above, and if that doesn't solve it, I would suggest running memtest overnight.

---

### Post by oldsoundguy on 2008-11-17
there are also "issues" with 8.10 and NVidia drivers.  LOTS of issues.  Check the blog at Envy for the latest.  There ARE new NVidia drivers on the near horizon.

---

