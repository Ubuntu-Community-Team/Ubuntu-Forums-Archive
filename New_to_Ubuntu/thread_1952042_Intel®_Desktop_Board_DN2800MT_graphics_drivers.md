---
title: "Intel® Desktop Board DN2800MT graphics drivers"
date: 2012-04-03
forum: New to Ubuntu
---

### Post by m2rt on 2012-04-03
Hello!

I see that Ubuntu does not support Intel® Desktop Board DN2800MT. It does not have the pvr graphics drivers.

Though Meego has those.

Is it possible to port them to ubuntu? I would most definately prefer to run ubuntu, as I have had too many problems with meego...

I downloaded the rpm drivers from here: [http://download.meego.com/live/MeeGo:/1.2.0:/CedarTrail:/non-oss/MeeGo_1.2.0_CedarTrail/i586/](http://download.meego.com/live/MeeGo:/1.2.0:/CedarTrail:/non-oss/MeeGo_1.2.0_CedarTrail/i586/)

I converted them to deb and installed them. After reboot the screen was black. Maybe there are unmet dependancies? Is there a point to try to continue to get the drivers to run on ubuntu without expert knowledge about linux?

Should I just give up and start using meego? (actually its a small project that I am doing and I am going to build 15 systems with this motherboard)

Can anybody give me directions towards the end goal? If the drivers get ported to ubuntu, then I am sure that there are a lot of happy people...

Also, check this: [http://comments.gmane.org/gmane.comp.freedesktop.xorg.drivers.intel/8816](http://comments.gmane.org/gmane.comp.freedesktop.xorg.drivers.intel/8816)

---

### Post by PhilTroy on 2012-04-16
Hi!

Would you please let me know about anything you figure out about using Ubuntu with the dn2800MT.  My direct email address is [email]phil@philtroy.com[/email]

I too do not wish to use meego.  I have found on the internet that linux 3.3 is supposed to handle the dn2800mt and I have tried updating the kernel to use 3.3 (following ubuntu instructions) but it has not helped.  I also tried creating an xorg.conf file to specify the 1920x1080 resolution I wish to get, with the result that I get a black screen.  I will fix that tonight with a ubuntu (actually lubuntu) installation usb key.

Thanks . . .

Phil

---

### Post by ballone on 2012-05-09
Hi. You need a kernel with DRM GMA3650 support enabled.
I don't know if the ubuntu Kernel have this.

best regards

---

