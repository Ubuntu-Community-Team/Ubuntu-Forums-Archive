---
title: "Hard disk problem detected"
date: 2012-04-10
forum: New to Ubuntu
---

### Post by pqku on 2012-04-10
Hi all ,

A window pops up and told me Hard disk problem detected.
So i clicked on Examine.

Then i can see smart status : disk failure is imminent.
So i clicked on smart data
here i can see

Reallocated sector count -----> failing

Current pending sector count ---> warning, value 2740

What does it mean ?

Thank you

---

### Post by Grenage on 2012-04-10
It basically means that your hard drive is generating bad sectors, and the drive cannot reallocate them - which means that you need to backup your data asap, and replace the drive.

---

### Post by zeljkojagust on 2012-04-10
First install smartmontools:
```
sudo apt-get install smartmontools
```

Than with fdisk check which is the failing disk:
```
sudo fdisk -l
```

For instance if failing disk is /dev/sdb, execute smart test by executing the following command:
```
smartctl --test=long /dev/sdb
```

Check test completion by executing following command:
```
smartctl -a /dev/sdb
```

When completed, paste the result of previous command here:
```
smartctl -a /dev/sdb
PASTE THE OUTPUT IN THIS POST
```

If you have any questions be free to ask.

---

### Post by pqku on 2012-04-10
Thanks for your help


Than with fdisk check which is the failing disk:
 	Code:
 	sudo fdisk -l 
How can i know which one is failing ?

---

### Post by zeljkojagust on 2012-04-10
Paste the output of "fdisk -l" here, and we'll see which one.

---

