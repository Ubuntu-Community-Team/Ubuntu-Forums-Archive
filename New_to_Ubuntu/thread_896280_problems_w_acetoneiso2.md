---
title: "problems w/ acetoneiso2"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by fignig on 2008-08-21
it always says that i can't mount the image. i'm trying to mount a .bin it's actually a game. and i've already added my username to the fuse group and all that. i keep trying to mount the .bin image and it keeps saying i can't. can anyone help, and it refers me to the help page and i did everything it said...

---

### Post by cariboo on 2008-08-21
The only way you can mount a bin/cue file is to convert it to an iso and then mount it. You can use one of the cd burning programs eg: brassero, gnomebaker or k3b to convert it to an iso.

Jim

---

### Post by bulletxt on 2008-08-21
AcetoneISO can directly convert it to iso or even better extract the image to a folder. no need to use other apps ;)

---

### Post by fignig on 2008-08-21
still the same problem arises. i can't seem to convert or mount this .bin file...

---

### Post by fignig on 2008-08-21
Error, could not mount image.

Solution:
[http://acetoneiso2.svn.sourceforge.net/viewvc/*checkout*/acetoneiso2/src/manual/manual.html](http://acetoneiso2.svn.sourceforge.net/viewvc/*checkout*/acetoneiso2/src/manual/manual.html)

is the error message.



Process Error Code: 255
This is error is mostly because the image you are trying to convert is already ISO-9660.
To check, open a terminal and type: file nameimage.xxx
If it is already ISO-9660, there is no need to convert it. Simply Extract it or Mount with AcetoneISO2.

is the error message when i try to convert it, even tho it is a .bin file it keeps lying to me telling me it's a .iso...

---

### Post by bulletxt on 2008-08-21
if you type from terminal:
file nameimage.xxx

what does it say? please output message

---

### Post by yrelle on 2011-06-26
ellery@Ubuntu-Latitude-D620-Ellery:~/Downloads$ file OSXLionDP4.dmg
OSXLionDP4.dmg: xar archive - version 1

---

### Post by Perfect Storm on 2011-06-26
Archaeology is an exciting and noble thing, except when digging up old threads from the past on forums.


Thread closed.

---

