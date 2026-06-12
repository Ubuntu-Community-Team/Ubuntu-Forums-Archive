---
title: "Installing DVD drivers"
date: 2012-11-01
forum: New to Ubuntu
---

### Post by graphicsmanx1 on 2012-11-01
Is there a tutorial or standard way to install drivers off a CD??  Id like to install my mobo's cd drivers for the onboard gpu

---

### Post by CharlesA on 2012-11-01
You shouldn't have to install anything off a CD. If your onboard GPU requires driver, there should be a pop up showing any additional drivers you can install.

---

### Post by ibjsb4 on 2012-11-01
I have swapped cd/dvd drives around and have yet to need to do anything but plug them in.  Are you sure you need drivers?

Edit:  I believe I misunderstood the question.  oops

---

### Post by jerome1232 on 2012-11-01
It doesn't quite work like that, in linux many of the drivers you need are included with the kernel, likely the Linux version of your gpu's drivers are already being used.

Are you experiencing problems that make you think you are lacking drivers?

---

### Post by graphicsmanx1 on 2012-11-01
No Im trying to get all my ducks in a row since this will be my first ubuntu build for a rip station.  Im installing a RAID 1 with 1TB drives to rip images for work.

---

### Post by jerome1232 on 2012-11-01
If nothing is listed under Additional Drivers in System Settings and your not experiencing any problems, then your ducks should all be in a row.

---

### Post by Mark Phelps on 2012-11-01
> **graphicsmanx1 said:**
> Is there a tutorial or standard way to install drivers off a CD??  Id like to install my mobo's cd drivers for the onboard gpu

Those drivers are ONLY for MS Windows -- and will NOT work in Linux.

The onboard GPU will be detected automatically.  If that is the ONLY video chipset you have on the PC, and you're seeing a desktop -- the hardware has been detected and the drivers already installed.

Linux is not like MS Windows -- you don't follow installation by immediately hunting around for drivers; instead, the proper drivers are found and installed automatically during initial setup.

---

### Post by graphicsmanx1 on 2012-11-01
> **Mark Phelps said:**
> Those drivers are ONLY for MS Windows -- and will NOT work in Linux.

The onboard GPU will be detected automatically.  If that is the ONLY video chipset you have on the PC, and you're seeing a desktop -- the hardware has been detected and the drivers already installed.

Linux is not like MS Windows -- you don't follow installation by immediately hunting around for drivers; instead, the proper drivers are found and installed automatically during initial setup.

thanks thats good to know..  If I install my dual GPUs will they detect the drivers too?  guess so as others have stated

---

### Post by Mark Phelps on 2012-11-02
> **graphicsmanx1 said:**
> thanks thats good to know..  If I install my dual GPUs will they detect the drivers too?  guess so as others have stated

Depends on what you mean by "dual GPUs".

If you mean two of the same chipsets, to run them in parallel, then you mean something like EyeFinity (AMD).  You need to ask specifically about that -- as I don't know if there is Linux support for that, as that tends to be provided by the Restricted AMD drivers.

If you mean different chipsets, as in one being Intel and the other AMD, that could be Hybrid Graphics -- and that is generally not supported well in Linux.  Once again, you would need to ask specifically about that.

---

