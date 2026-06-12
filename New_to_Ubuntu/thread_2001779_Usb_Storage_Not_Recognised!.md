---
title: "Usb Storage Not Recognised?!"
date: 2012-06-11
forum: New to Ubuntu
---

### Post by xgalexyx on 2012-06-11
I have an old Dell Inspire 8600 which was running quite slow so i decided to put  lubuntu on as i have previously used ubuntu and lubuntu is meant to be similar, but more lightweight and quicker on older machines. Lubuntu installed fine and i went to plug in a usb pen drive which contained a few documents i wanted to transfer. When i plugged it in the usb its LED turned on, but there was no notification or any sign of it existing. 

I tried "fdisk -1" and it replied 

"fdisk: invalid option -- '1'"

Is there a way i can get this USB recognised with no internet access on the dell 8600?

---

### Post by xgalexyx on 2012-06-11
Or could it be not working because of the lack of an internet connection, through which it would download appropriate drivers?

---

### Post by Cheesemill on 2012-06-11
What's the output of:
```
sudo fdisk -l
```
(It's a lowercase L, not the number 1).

---

### Post by xgalexyx on 2012-06-11
Ok so it's not lubuntu, or at least i don't think it is. I can use my phone and plug the usb in to mount the micro sd inside my phone, with no problems. It appears the laptop simply doesn't recognize that memory card.

---

### Post by LukeMorrison on 2012-06-11
I think the command you are looking for is the following:
 
```
sudo fdisk -l
```
 
I've had trouble using that command without sudo. Also, it is a lower case "L", not the number one
 
Ah...beaten to it, by Cheesemill

---

