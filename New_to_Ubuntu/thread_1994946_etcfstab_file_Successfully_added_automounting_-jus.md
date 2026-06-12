---
title: "/etc/fstab file: Successfully added automounting -just to tidy it up now"
date: 2012-06-03
forum: New to Ubuntu
---

### Post by bikefreakvinnie on 2012-06-03
Hi Folks,
In Ubuntu server 12.04 I've edited the /etc/fstab
this is to have auto mount points for usb hard drives...
However on start up if one is turned off I get an error! Is it possible to add somewhere to mount these drives **_if_** present?

If anyone wants anymore details let me know...

thanks if anyone can help

---

### Post by Plueonic on 2012-06-03
You can use the *nofail *optionto ignore if the device is absent[I].
[/I]

---

### Post by bikefreakvinnie on 2012-06-03
Great thankyou Plueonic i presume if i put in the following:

dev/divice /media/movies ntfs nofail,defaults 0 0

---

### Post by Plueonic on 2012-06-03
> **bikefreakvinnie said:**
> Great thankyou Plueonic i presume if i put in the following:

dev/divice /media/movies ntfs nofail,defaults 0 0
Yep

---

### Post by bikefreakvinnie on 2012-06-03
I've since added:

defaults,nobootwait

seem grand so far!

---

### Post by Plueonic on 2012-06-03
Glad you found a solution :)

---

### Post by bikefreakvinnie on 2012-06-03
Thanks a mil for all that!

---

