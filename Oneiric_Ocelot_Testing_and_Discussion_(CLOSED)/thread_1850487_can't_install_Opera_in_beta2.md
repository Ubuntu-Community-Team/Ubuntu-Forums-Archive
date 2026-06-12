---
title: "can't install Opera in beta2"
date: 2011-09-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by nairias on 2011-09-26
I have installed beta 2 of 11.10 and downloaded .deb of Opera 11 (the most up-to-date from the opera.com (opera_11.50.1074_amd64.deb), 64bit - matching the version of Beta2 as well as previous version of Opera). Previously, on 11.04 I had absolutely no problem with Opera. In 11.10 the .deb file launches, Ubuntu Soft Center opens, thinks for several seconds and announces: "Internal Error. The file opera.....deb could not be opened"

I installed 11.10b2 on btrfs partition at first, then formatted to ext4 and fresh install on ext4. With 11.04 on both btrfs and ext4 Opera installation went w/o any problems.

I'm stuck with Firefox for now :)

---

### Post by mc4man on 2011-09-26
The is something about the construct of that deb that Sc & gdebi don't like
 (fails some debian test
You can use the dpkg command instead 
sudo dpkg -i /path/to/whatever.deb

Ex. here 
sudo dpkg -i ~/Downloads/opera_11.51.1087_i386.deb

---

### Post by nairias on 2011-09-26
works perfectly, thx

---

