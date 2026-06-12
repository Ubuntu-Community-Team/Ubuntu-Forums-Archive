---
title: "[SOLVED] Safe to uninstall xserver xorg core?"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by klemperal on 2008-10-12
I'm trying to install  an older version, but I have this fear that once I uninstall the current xserver xorg core that all my hardware will just stop working.  Is it safe for me to uninstall xserver xorg core?  Anything I should keep in mind?

---

### Post by sokopok on 2008-10-12
Why not. It will just uninstall You can always reinstall it. But you could also just try this: in Synaptic select the package and then go to the menu "Package/Force Version"

---

### Post by klemperal on 2008-10-12
I tried force version earlier, but the core version won't go far back enough for an older driver package I need.  By the way, I notice that when I mark the core for removal it marks a whole bunch of other xorg related packs for removal as well.  Should I be concerned about all these random packages?  Should I keep track of them so I can reinstall them, or does it matter?

---

### Post by sokopok on 2008-10-12
The other packages are input and video drivers.
If you use synaptic you can experiment a bit. It will tell you what actions it wants to perform berfore actually touching your system. So select uninstall, it'll tell you what it wants to remove, then select reinstall and see what happens (actually, it'll just reinstall everything, but try it anyway, it's very informative (don't apply the changes in between, first make sure you get what you want, then apply).

---

### Post by klemperal on 2008-10-12
I see.  Checking out the details of the uninstall is very informative.  I just saved all the packages to be removed as a text file so if I run into any problems I can always go back and reinstall them.  Thanks a lot for the help my friend.

---

### Post by klemperal on 2008-10-12
Alright, I seem to have run into a little trouble here.  First, I completely removed the current version of xserver xorg core.  Second, I tried installing an older version.  However, the older version not install all the way.  It gives me an error "Error:failed to install all dependencies (broked cache)."  It sauggests I run ```
sudo apt-get install -f    
``` but this upgrades the old package to the new one.  Any ideas?

---

### Post by sokopok on 2008-10-12
Xorg depends on many packages, so it is possible that you can't go back to an older version, as this would probably break your setup. Don't mess too much with the package system, you'll regret it later (I speak from experience, believe me).
Why would you want such an old version anyway?

---

### Post by klemperal on 2008-10-12
Because the current version of xorg intel video doesn't work with my intel 945 chip very well--at least not on 3D games anyway.  My computer will lock up during them and require hard restarts as a result.  I did some digging around and found that other people with an intel 945 chip were experiencing the same thing with the current and bleeding edge xorg intel video packs.  The solution for them seemed to be going back to the older version.

---

