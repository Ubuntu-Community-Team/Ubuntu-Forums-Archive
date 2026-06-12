---
title: "flash media card...where are you?"
date: 2012-01-07
forum: New to Ubuntu
---

### Post by syerges on 2012-01-07
when I plug in my sd card reader with a card in it, it acknowledges that it's there but I can't seem to find the thing. Where do I look for the card in my file system? I already feel stupid so no name calling neccessary..lol

---

### Post by syerges on 2012-01-07
found the card... won't let me mount it... I want to format it... is it possible to format without mounting?

---

### Post by rui2312 on 2012-01-08
First use "sudo fdisk -l" to find your sd card's device symbol.
Then you can use "mkfs -t vfat /dev/sd*" to format it.(sd*is your sd card's device.
Regards

---

### Post by Double.J on 2012-01-08
> **rui2312 said:**
> First use "sudo fdisk -l" to find your sd card's device symbol.
Then you can use "mkfs -t vfat /dev/sd*" to format it.(sd*is your sd card's device.
Regards
 +1

Just to answer your second Question, no, in fact you'd have to unmount it to format it. I'd just add be sure to double check which letter you put in /dev/sd[COLOR="Red"]x[/COLOR]- x should almost never be a ;)

---

### Post by syerges on 2012-01-18
my card was garbage as well as the second one I tried, the third however was fine...:D

---

