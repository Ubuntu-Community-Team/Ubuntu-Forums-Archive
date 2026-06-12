---
title: "Wanna Play MineCraft with ATI Radeon HD 5450"
date: 2012-02-18
forum: New to Ubuntu
---

### Post by LeetPlex on 2012-02-18
I Cant Play MineCraft I Know that my Graphiccard is disabled so im in xorg.conf and im trying to add The Driver but i dont Know what the Name is...

---

### Post by LeetPlex on 2012-02-18
```
Section "Device"
    Identifier    "Default Device"
    Drivers    "ATI" // Unknow 
    Option    "NoLogo"    "True"
EndSection
```

---

### Post by anewguy on 2012-02-18
ATI drivers are a tricky beast at best right now. What you should do is:

- get rid of the xorg.conf file - delete it

- be sure you are connected to the net, then:

go to additional drivers - if you are running the default 11.10 Ubuntu you need to go to the top of the dash on the left which will say "Dash Home" when your mouse is on it, click it, type in add in the search box, then click on additional drivers.  This may take a while as it will look at the net and local and then recommend any drivers it thinks you may need.  You'll probably get a driver listed for your video - enable it and reboot.  

That should get your video driver installed.  Next go to the [Ubuntu gaming and leisure forum]("http://ubuntuforums.org/forumdisplay.php?f=93") for more help with minecraft and Ubuntu.

Dave ;)

---

