---
title: "Compiz failure in HH with open drivers (worked in GG)"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by AncientPC on 2008-04-27
I have a Radeon Mobile x300 (fully 3D support by open source drivers via [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)) and am unable to get Compiz working in HH with the open source drivers despite it working in GG.

glxinfo reports that I support direct rendering, glxgears gives me ~750fps.

When I try to enable advanced desktop effects with open drivers it gives me an "Desktop effects could not be enabled." error message.

Compiz works with binary drivers, but binary drivers break other parts of my system so I would prefer not to use them.

Any suggestions?

---

### Post by AncientPC on 2008-04-27
I solved the problem by following these instructions: [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

Basically, Compiz blacklisted older ATI cards but you can modify the conf files to get around that.

On a side note, I noticed that xorg used a lot more cpu time under binary drivers than the open source ati drivers when running Compiz.  Under binary drivers, xorg usage was pegged 20 - 60%, under ati xorg usage is around 5 - 40%.

---

