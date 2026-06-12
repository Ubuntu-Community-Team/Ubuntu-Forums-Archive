---
title: "No additional drivers ?"
date: 2012-01-20
forum: New to Ubuntu
---

### Post by Lupajz on 2012-01-20
Hey I'm not getting any info for additional drivers in xubuntu 11.10 for acer 5535 with ati HD 3200 is it a bug or do I have to DL ati drivers from ati site ?

---

### Post by 3rdalbum on 2012-01-20
If it's a dual-GPU card, then unfortunately you can't use the proprietary drivers, and they won't appear in the Additional Drivers program.

Otherwise, they should. Have you refreshed the software list? If not, try:

```
sudo apt-get update
```

and then start Additional Drivers again.

---

### Post by Lupajz on 2012-01-20
> **3rdalbum said:**
> If it's a dual-GPU card, then unfortunately you can't use the proprietary drivers, and they won't appear in the Additional Drivers program.

Otherwise, they should. Have you refreshed the software list? If not, try:

```
sudo apt-get update
```

and then start Additional Drivers again.

Yea, worked :P But also I was trying to install post-release update, or whatever it is :P

---

### Post by Mark Phelps on 2012-01-21
> **Lupajz said:**
> Yea, worked :P But also I was trying to install post-release update, or whatever it is :P

The post-release drivers will not install.  Get lots of posts about this.

---

