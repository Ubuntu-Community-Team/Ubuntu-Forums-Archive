---
title: "VLC not play commercial DVD's"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Covalent Bond on 2008-06-04
Hardy Heron.  I know this has been posted before, and as instructed in these posts, I installed VLC and the restricted extras, and neither Totem or VLC will play a rented DVD.  Totem does not bother me, but I like VLC, and it worked fine in Gutsy.  What have I done wrong.  If I place a non-commercial DVD (exercise) the DVD plays fine.
TX CB

---

### Post by wolfen69 on 2008-06-04
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

```
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```
```
sudo apt-get install libdvdcss2
```

---

### Post by Covalent Bond on 2008-06-04
Wolfen69

SOLVED  Thanks for the quick response.  Your directions worked for both Totem and VLC.  As always, I appreciate the wealth of information I receive from the forum whether I post the question  or read info from other posts.

Again, thanks  CB

---

