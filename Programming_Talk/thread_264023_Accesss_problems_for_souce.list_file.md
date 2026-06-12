---
title: "Accesss problems for souce.list file"
date: 2006-09-24
forum: Programming Talk
---

### Post by kuatous on 2006-09-24
yeah so me and buddies are using ubuntu as a server stand alone we tried to modify the source.list file and its saying we do not have permission because we are not the owner. tryed to reconfig nothin changed gonna try to reinstall to see if maybe there was a file that got screwed up but at this time any help would be very much appreciated.[-o<

---

### Post by wieman01 on 2006-09-24
Add "sudo" and key in your user password when prompted:
> sudo gedit /etc/apt/sources.list

---

