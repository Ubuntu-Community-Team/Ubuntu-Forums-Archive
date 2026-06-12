---
title: "uninstalling vmware?"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by ipatec on 2008-05-07
I've installed vmware server on my Ubuntu 8.04. Actually the installation failed and now I don't know how to remove all the files extracted.
Any advice?

---

### Post by upthelum on 2008-05-07
Try removing it from Synaptic.

---

### Post by ipatec on 2008-05-07
Only the xorg for vmware appear in Synaptics...

---

### Post by upthelum on 2008-05-07
Well if you want to get some screenshots or output of the error your getting i'll bump it for you.

---

### Post by ipatec on 2008-05-07
Here is a part of installation copied from Terminal (I don't know how to copy all because more than I paste here doesn't appear)

Edit bodhi.zazen : clipped out the long output, the majority of which was the VMWare license agreement.

---

### Post by bodhi.zazen on 2008-05-07
To get VMWare working, see this thread : 

[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)
 
If you want to remove vmware, run [FONT=monospace]

[/FONT]```
sudo vmware-uninstall.pl
```Not sure of the location of this script, it may be in the same location as the install script or in /usr/bin/vmware-uninstall.pl

---

### Post by shifty_powers on 2008-05-16
i just entered as is and it worked ;) cheers

---

