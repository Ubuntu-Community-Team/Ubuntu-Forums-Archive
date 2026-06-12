---
title: "Create an Installable Any/Distro or Ubuntu for Hackberry or ANYdest,  ARM/Intel/ANY"
date: 2012-12-12
forum: New to Ubuntu
---

### Post by acatto on 2012-12-12
Fellows,
I've used Ubuntu for a while now and Linux in general for more than 14 years, yet !!! I never got into "creating an Ubuntu or Any Linyx Distro" for another destination system.
 
Just got myself a Hackberry A10, I have to depend on other Linux guru's to come out with their Images so that I can DD'em out to a flash drive.
 
How do I do that myself ???
 
Is there any set of general instruction for any Linux Distro or specifically for Ubuntu to allow.... given its source code or iso or something... some start.... creating either a custom ISO or in my case some ARM/Ubuntu for say... Hackberry A10 or Raspberry Pi or ANY destination ARM....
 
ARM is like a mushroom is taking over evrerything now and I want to learn now to be independent and create Linux distros' for any of thse devices or any architecture for that matter.
 
How do you gurus do ?
 
Thank you, Grazie, Gracias.

---

### Post by Cheesemill on 2012-12-12
I know this isn't really an answer but a lot of the time if it's possible to install a distro on an ARM device then the developers have already made the required images available. Both Debian and Ubuntu have ARM images on their download pages.

If you want to try creating your own images then Debian is probably the best place to start. Take a look a [debootstrap]("http://wiki.debian.org/Debootstrap"), this installs a basic linux system into a directory on your running machine, the target directory in your case would be the empty SD card where you are creating the root filesystem for your device.

---

