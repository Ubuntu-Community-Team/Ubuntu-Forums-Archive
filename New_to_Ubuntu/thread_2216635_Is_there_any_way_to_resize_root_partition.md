---
title: "Is there any way to resize root partition?"
date: 2014-04-13
forum: New to Ubuntu
---

### Post by kr4k3n2 on 2014-04-13
Is there any way to resize ubuntu root partition? ](*,)
i want decrease the root partition size

---

### Post by monkeybrain20122 on 2014-04-13
Yes, with gparted. What exactly is your layout and what do you want to do? Typing in red bold fonts but supplying little information is not a very smart way to ask for help, just saying.

---

### Post by kr4k3n2 on 2014-04-13
i want to decrease the size of root partition :)

---

### Post by monkeybrain20122 on 2014-04-13
yeah on the left or the right? Are you dual booting? What does the layout look like now? More info please.

---

### Post by lisati on 2014-04-13
> **monkeybrain20122 said:**
> Yes, with gparted. What exactly is your layout and what do you want to do? Typing in red bold fonts but supplying little information is not a very smart way to ask for help, just saying.
Agreed:
[LIST=1]
[*]More information would be useful
[*]Using large red lettering is NOT a good way of asking for help
[/LIST]

---

### Post by kr4k3n2 on 2014-04-13
no just ubuntu :)

---

### Post by kr4k3n2 on 2014-04-13
heard of some live cd partitioning? how does it work? will it help?

---

### Post by monkeybrain20122 on 2014-04-13
Well first order of business. Boot into a live usb (or live dvd) and open gparted, take a screenshot of your hard drive layout and post here. gparted would be the tool for resizing partitions and it is in the live cd.

---

### Post by kr4k3n2 on 2014-04-13
this is bad right? i lost win7 while installing ubuntu everything messed up :(
[IMG]https://fbcdn-sphotos-c-a.akamaihd.net/hphotos-ak-prn2/t31.0-8/1291963_1424775014446521_4276355127429499073_o.jpg[/IMG]

---

### Post by kr4k3n2 on 2014-04-13
also please suggest me a standard partition i am planning to reinstall win7 (dual-boot)

---

### Post by monkeybrain20122 on 2014-04-13
So what do you want to do?

---

### Post by kr4k3n2 on 2014-04-13
i just want to decrease the size of that partition :)

---

### Post by monkeybrain20122 on 2014-04-13
So you just want to shrink /dev/sda6 on the right end? That would be easy. 
You have to do these operations in the live usb/cd
1) make sure that /dev/sda6 is unmounted (it should be, unless you have mounted it)
2) right click on it, choose Resize/Move
3) Supply the info for new size
4) click resize/move
5) click the check mark on the top to apply all operations.
 Then just wait. It shouldn't take long as you are shrinking the empty end and don't interrupt it.

---

### Post by kr4k3n2 on 2014-04-13
[size=4]**thank you.**[/size]

---

