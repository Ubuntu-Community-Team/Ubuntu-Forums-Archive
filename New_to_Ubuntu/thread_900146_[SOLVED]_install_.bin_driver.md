---
title: "[SOLVED] install .bin driver"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by no_idea on 2008-08-25
I've downloaded the driver for a wireless router from their official site and it's a bin file. I've chmod 777 and tried ./file.bin and it says it cannot execute it, so I've run file file.bin and it says it's a data file. Ok so I figured it's an image file and I tried mounting it in MagicISO and it says that it's not a valid image file :confused: No what?
Help me please!!

---

### Post by lisati on 2008-08-25
Occasionally you have to chmod +X a file to make it executable. Did the installation instructions say to actually run the file?

---

### Post by no_idea on 2008-08-25
nothing.. it's still seen as a data file

---

### Post by Gregmond on 2008-08-25
I might be on the wrong track but.... whenever I have seen a .bin file for a router its actually a firmware upgrade for the router and you need to log into the router and import it. Drivers as such are normally different.

---

### Post by no_idea on 2008-08-25
So you're saying i should try and download a real driver for the Linksys router (my router is Linkys), Gregmond. But I can't find anything and I don't have an installation cd :( Thanks anyway...

---

### Post by sonofusion82 on 2008-08-25
do you really need a driver for the router?
i also thought that router is an standalone device and PC should access to them via standard web or telnet interfaces.

---

### Post by no_idea on 2008-08-25
You're right. Terrible mistake I've made.. Any way problem solved somehow..

---

### Post by silverglade00 on 2008-08-25
On my Linksys router, the .bin files are firmware files. It is indeed a kind of data file, but it is also a driver in a sense. Basically, the .bin is a file containing the OS, applications, and data needed to run the router. To use it on my router, I log onto the web interface for the router and then go to the firmware upgrade section. Then I backup my existing firmware with the backup feature and apply the upgraded one.

---

