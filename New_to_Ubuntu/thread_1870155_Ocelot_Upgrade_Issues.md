---
title: "Ocelot Upgrade Issues"
date: 2011-10-26
forum: New to Ubuntu
---

### Post by thelowerrhythm on 2011-10-26
I am relatively new to Linux and began the upgrade to Ocelot from Narwhal this afternoon. During the "Installing" portion of the upgrade, the machine lost power. Now when I try to boot it goes to a login screen (with black background and no graphics). At this screen, the machine automatically freezes.

I'm not sure how to get the installation back on track.

---

### Post by khelben1979 on 2011-10-27
Have you tried to boot into safe mode? 

And once you have a working text console you can reconfigure the X server so you can get back to working X server. ```
Xorg -configure
```

---

