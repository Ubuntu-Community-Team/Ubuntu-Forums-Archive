---
title: "Apt-get doesn't work"
date: 2005-02-01
forum: Repositories &amp; Backports
---

### Post by zergberg on 2005-02-01
Having installed my ifty new ubuntu system, I tried to use apt-get to install several applications supposedly available according to the unofficial guide-thing.
However, on attempting the install of various things (xmms, qtparted), I got errors. Xmms said that it was part of another repository, and that qtparted was not found. The text to change as suggested in the "Add Extra Repositories" section of the guide did not help either, as said text was not in the document it pointed to. Do I need to be connected to the internet in order to install the other applications, or is something else wrong?

---

### Post by dusu on 2005-02-01
After you have modified your /etc/apt/sources.list as you said you did, and 
then doing 
```
sudo apt-get update
```
the command 
```
 sudo apt-get install xmms 
```
should install xmms.

And yes, you have to be connected to the internet, since the packages are downloaded from [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)

---

### Post by ciandro on 2009-12-06
I'm trying the same thing to see if it works!
;)

---

