---
title: "Ubuntu overheated my laptop, then proceeded to break itself"
date: 2014-01-14
forum: New to Ubuntu
---

### Post by xxxbbakerxxx on 2014-01-14
So, a few hours ago, I decided to get my feet wet in linux, and install ubuntu alongside Windows 7. 

After a few minutes of use, my laptop shut off on its own, and was extremely hot to the touch. (This was an issue I'd never had before now, and I didn't have it on a surface where the ventilation was blocked or something like that).

Now, whenever I boot into ubuntu, it just hangs at a blank purple screen.

My version is 12.03


Is there an explanation for my laptop overheating, and is there a way to return ubuntu to a functioning state without completely reinstalling it?

---

### Post by QIII on 2014-01-14
Hello!

Do you mean version 12.04.3?

Can you tell us the specifications of your machine?

---

### Post by xxxbbakerxxx on 2014-01-14
1.6 GHz Intel I7

Intel HD 3000 GPU

8GB RAM

Not the most glamourous thing, but it should be enough for ubuntu, shouldn't it?

And yes, I meant 12.04.3

---

### Post by xxxbbakerxxx on 2014-01-14
Update, I tried booting again, and this time it seems to be working, but my laptop's still running pretty hot compared to windows. Is there a setting I should be looking at?

EDIT:And...I try installing a program and it overheats again.

---

### Post by QIII on 2014-01-14
Does your machine also have a dedicated GPU?

---

### Post by xxxbbakerxxx on 2014-01-14
No, sir.

---

### Post by mastablasta on 2014-01-14
well that's strange then. because intel is well supported.

if this is one of latest intel CPU then you might want to load newer kernel: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

can you copy and post a few outputs from commands mentioned here so we can see the full specs? : [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

particulary the sudo lshw command.

---

