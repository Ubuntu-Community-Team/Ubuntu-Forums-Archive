---
title: "Live CD Won't Boot"
date: 2014-01-26
forum: New to Ubuntu
---

### Post by mlv213 on 2014-01-26
hello!

I burned the 13.10 .iso onto a CD and started my laptop with it in. after booting, my screen goes directly to the purple loading page with logo, and if I press any of the F keys, it gives me the code "calling:test-builtin 
error reading lib/udev/hwdb.bin: No such file or directory
load module index
unload module index
unable to open '/dev/sda'"

it eventually brings me to a builtin shell, busybox. 

any ideas for a fix?

---

### Post by DuckHook on 2014-01-26
Looks like a bad burn. If using CD, please torrent ISO rather than download, as torrent is a self-auditing/correcting technology. Torrent from Ubuntu site and no other. If you cannot torrent for some reason, then make sure you MD5 the ISO, and checksum the burned image. Instructions [here]("https://help.ubuntu.com/community/BurningIsoHowto"). Once confident of burn, run session as a LiveDVD/USB to make sure everything is working before installing. This includes running gparted (be careful!) to see if all HDDs are recognized. A good installation howto is [here]("https://help.ubuntu.com/community/Installation").

---

### Post by squakie on 2014-01-27
I can't see myself how you could have gotten that far if indeed you downloaded the normal Ubuntu 13.10 image and "burned" the ISO to a CD.  I don't believe the normal ubuntu (not lubuntu, xubuntu, the alternate cd, etc) image would fit on a CD - it has to be a DVD.  So, did you really use a CD?  At what point do you get the purple screen - have you gotten to the selection screen for "try ubuntu" or "install ubuntu"?  If so, which did you choose?

---

