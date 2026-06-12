---
title: "Obtain ownership of old files using live distro"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by Gary Nored on 2008-09-14
I'm trying to copy files from an old Ubuntu (Drake?) hd from a computer that died (motherboard croaked). I've put the drive in a housing and connected it to a new machine via usb. Using the latest live distro, I can see the drive, but I cannot copy anything from my old home directory. 

How can I obtain ownership of these files so I can copy them to another drive?

TIA -- Gary

---

### Post by gkestrel on 2008-09-14
Have you tried using nautilus as root, in a terminal type 

gksudo nautilus

this will open nautilus with root priviledges so be very careful what you do when you have it open. This should allow you to copy the files to were you want them to be.

---

### Post by k33bz on 2008-09-14
you should be able to:


sudo chown -R username.usergroup /destination/of/directory/to/be/changed

then copy them over, which ever way is more comfortable to you, via GUI or Terminal

---

