---
title: "[SOLVED] Fresh install image on USB"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by rideburton56 on 2008-11-16
I am planning on doing a fresh install of intrepid, and wanted to give ubuntu studio a try. It seems that it can only come as a DVD.  I dont have a dvd burner, just a CD burner.  Should I download basic intrepid, and then install extra packages, or can i put the ubuntu studio image on a USB and do a fresh install from there? Thanks

---

### Post by jimmy the saint on 2008-11-16
Install Ubuntu then use apt to do the rest

after ubuntu is installed

```
sudo apt-get update
```
to update package listings

```
sudo apt-get install ubuntustudio-desktop
```

that will install the ubuntu studio system and when you log in you can choose that as your session

---

### Post by rideburton56 on 2008-11-16
thanks!

---

