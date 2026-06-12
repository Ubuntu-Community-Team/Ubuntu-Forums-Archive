---
title: "build essential (along w/ other things) problem."
date: 2008-08-27
forum: New to Ubuntu
---

### Post by determinedblkman on 2008-08-27
ok, the short. i got linspire and it doesnt pick up my wireless card(linksys wmp54g ver.4). i tried ndiswrapper, but it's not loading write-cant find the 'include' directory, and '.config' file. i tried loading the build essential tar i got, but that aint building right. i not online to use apt-get so i feel like i in between a rock & a hard space. help me someone PLEASE!!

---

### Post by Crafty Kisses on 2008-08-27
What XP driver did you end up getting for your card? (version)

---

### Post by mcduck on 2008-08-28
Build-essential should be included on the Ubuntu CD's, just enable the disk as a repository (in software sources) and use apt-get to install build-essential.

```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```

---

