---
title: "Eclipse won't update"
date: 2011-03-10
forum: Programming Talk
---

### Post by MountainX on 2011-03-10
I haven't used Eclipse since last fall. I opened it today and went to check for updates.

First I got this error:
> No repository found at [http://community.polarion.com/projects/subversive/download/eclipse/2.0/weekly-site/](http://community.polarion.com/projects/subversive/download/eclipse/2.0/weekly-site/)

I disabled subversive in the "Available Software Sites" and tried again. 

This time, I got the following error:

> Cannot complete the install because of a conflicting dependency.
  Software being installed: Eclipse Platform SDK 3.6.2.M20110210-1200 (org.eclipse.platform.sdk 3.6.2.M20110210-1200)
  Software currently installed: Shared profile 1.0.0.1284709157554 (SharedProfile_epp.package.java 1.0.0.1284709157554)
  Only one of the following can be installed at once: 
    Equinox Provisioning Director 2.0.0.v20100525 (org.eclipse.equinox.p2.director 2.0.0.v20100525)
    Equinox Provisioning Director 2.0.2.R36x_v20100823 (org.eclipse.equinox.p2.director 2.0.2.R36x_v20100823)
    Equinox Provisioning Director 2.0.3.R36x_v20101117-1018 (org.eclipse.equinox.p2.director 2.0.3.R36x_v20101117-1018)
  Cannot satisfy dependency:
    From: Shared profile 1.0.0.1284709157554 (SharedProfile_epp.package.java 1.0.0.1284709157554)
    To: org.eclipse.equinox.p2.director [2.0.2.R36x_v20100823]
  Cannot satisfy dependency:
    From: Equinox p2 Provisioning 2.0.1.r361_v20100903-897HFa-FX0z-z-ntoaavz0JPX628 (org.eclipse.equinox.p2.user.ui.feature.group 2.0.1.r361_v20100903-897HFa-FX0z-z-ntoaavz0JPX628)
    To: org.eclipse.equinox.p2.director [2.0.3.R36x_v20101117-1018]
  Cannot satisfy dependency:
    From: Eclipse Platform SDK 3.6.2.M20110210-1200 (org.eclipse.platform.sdk 3.6.2.M20110210-1200)
    To: org.eclipse.equinox.p2.user.ui.feature.group [2.0.1.r361_v20100903-897HFa-FX0z-z-ntoaavz0JPX628]

I disabled EPP Repository in the "Available Software Sites" and tried again.

Now I got this error:
> Cannot complete the install because of a conflicting dependency.
  Software being installed: Eclipse Platform SDK 3.6.2.M20110210-1200 (org.eclipse.platform.sdk 3.6.2.M20110210-1200)
  Software currently installed: Shared profile 1.0.0.1284709157554 (SharedProfile_epp.package.java 1.0.0.1284709157554)
  Only one of the following can be installed at once: 
    Eclipse Platform 3.6.0.v201006080911 (org.eclipse.platform 3.6.0.v201006080911)
    Eclipse Platform 3.6.1.v201009090800 (org.eclipse.platform 3.6.1.v201009090800)
    Eclipse Platform 3.6.2.v201102101200 (org.eclipse.platform 3.6.2.v201102101200)
  Cannot satisfy dependency:
    From: Shared profile 1.0.0.1284709157554 (SharedProfile_epp.package.java 1.0.0.1284709157554)
    To: org.eclipse.platform [3.6.1.v201009090800]
  Cannot satisfy dependency:
    From: Eclipse Platform 3.6.2.r362_v20110210-9gF78Gs1FrIGnHDHWkEcopoN8AmxeZflGDGKQi (org.eclipse.platform.feature.group 3.6.2.r362_v20110210-9gF78Gs1FrIGnHDHWkEcopoN8AmxeZflGDGKQi)
    To: org.eclipse.platform [3.6.2.v201102101200]
  Cannot satisfy dependency:
    From: Eclipse Platform SDK 3.6.2.M20110210-1200 (org.eclipse.platform.sdk 3.6.2.M20110210-1200)
    To: org.eclipse.platform.feature.group [3.6.2.r362_v20110210-9gF78Gs1FrIGnHDHWkEcopoN8AmxeZflGDGKQi]

What should I do?

---

### Post by cartman_ on 2011-03-22
Try running eclipse with sudo. Update what you can (so packages in not user writeble places are updated) then run again as normal user so your private plugins (~/.eclipse) are updated as well.

I had a problem with the java platform ide. It could not overwrite the stuff in /opt/eclipse/ since its readonly for the normal user. So my guess is that eclipse tries to install this locally for the normal user (~/.eclipse), but you can not have the same packages twice thus the dependency conflict.

EDIT: This didn't help me either in the end. I didn't check if the plugins I installed are available until later when I found out that none of them are. Some plugin failed on start up with an illegal state exception saying some thing like "The main bundle has been updated. The IDE has to be restarted to finish installation." In the end I gave up on having eclipse in a non user writable place. Luckily I am alone on my machine but I don't know how would I solve this without complete reinstall.

---

