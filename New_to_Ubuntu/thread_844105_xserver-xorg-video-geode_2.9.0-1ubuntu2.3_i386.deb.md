---
title: "xserver-xorg-video-geode_2.9.0-1ubuntu2.3_i386.deb"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by Robynsveil on 2008-06-29
Got an update orange star on my panel requesting I update but downloading this file:
xserver-xorg-video-geode_2.9.0-1ubuntu2.3_i386.deb

The path:
[http://au.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-geode/xserver-xorg-video-geode_2.9.0-1ubuntu2.3_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-geode/xserver-xorg-video-geode_2.9.0-1ubuntu2.3_i386.deb)

generated a 404 error. Any way to get around this?

Thanks to all who might have a clue...

---

### Post by micduffy on 2008-06-29
I went to the preferences of the package manager (reachable from the orange star taskbar icon) and selected "Main Server" from the dropdown list where "Australian Server" was previously selected.

After this, Synaptic checked for packages again and I was able to complete the update successfully.

---

### Post by Robynsveil on 2008-06-29
> **micduffy said:**
> I went to the preferences of the package manager (reachable from the orange star taskbar icon) and selected "Main Server" from the dropdown list where "Australian Server" was previously selected.

After this, Synaptic checked for packages again and I was able to complete the update successfully.

Yup, worked a treat... thanks, mate....

---

### Post by von Stalhein on 2008-06-30
I looked in the [http://au.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-geode/](http://au.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-geode/) directory, and the version there is 2.2 rather than the 2.3 as pushed out in the update.

I wonder if it's a lag in updating? I know it's not major, but I was just curious :-)

I think I'll try ```
sudo apt-get update
``` as well as your most excellent suggestion above to sync the packages.

---

