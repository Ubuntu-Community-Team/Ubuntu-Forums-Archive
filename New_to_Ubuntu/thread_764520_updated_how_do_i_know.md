---
title: "updated how do i know"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by pardesi on 2008-04-24
hi i just updated from fiesty to gutsy ...how do i get to know that i actually have i mean while logging on with fiesty it used to show fiesty..or something like that...i find nothing with gutsy written on it here...nor do i see any change in the look

---

### Post by Vicfred on 2008-04-24
System > Administration > System monitor

take a look at the System tab

---

### Post by pardesi on 2008-04-24
it says fiesty :confused::confused:...and the update manager says there is nothing left to be updated

---

### Post by Rabindranath on 2008-04-24
Maybe try System > About Ubuntu..

---

### Post by pardesi on 2008-04-24
one thing is for sure though my update manager shows i have updated...but it is not atleast phsyically i mean i get to see only fiesty writtene everywhere and whatsoever no changes

---

### Post by Helios38 on 2008-04-24
sudo apt-get dist-upgrade


???

---

### Post by Rabindranath on 2008-04-24
Maybe you can try a fresh install. A fresh install is always better than an update. Maybe you can try Hardy when it is released. :)

---

### Post by pardesi on 2008-04-24
hmm.. i actually thought the other was better i mean an update....raeding some of the wikis

---

### Post by pardesi on 2008-04-24
also it wud be difficult to transfer all my data:(

---

### Post by Tatty on 2008-04-24
try ```
lsb_release -a
```

How did you upgrade?  the clincher would be to check your sources.list file.   post the output of ```
cat /etc/apt/sources.list
``` so we can see what repos you are using.

---

### Post by bran on 2008-04-24
> **pardesi said:**
> also it wud be difficult to transfer all my data:(

if you ever do get the urge to do a fresh install create a /home partition.  there is an article somewhere here on creating an new partition, copying the home partition to it then editing the fstab to point to the new /home.

how exactly did you do the update?

Bran

---

### Post by pardesi on 2008-04-24
sorry i soon realized that i hadn't upgraded just updated....now i am upgrading:guitar:

---

### Post by Tatty on 2008-04-24
> **pardesi said:**
> sorry i soon realized that i hadn't upgraded just updated....now i am upgrading:guitar:

:popcorn: let us know how it goes!

---

