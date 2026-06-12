---
title: "ddigikam and wastebin maximum"
date: 2013-01-24
forum: New to Ubuntu
---

### Post by miel on 2013-01-24
upon deleting images in Digikam, program announces:

"The wastebin has reached its maximum size!
Cleanup the waste bin manually."

in fact wastebin is empty and can be used withiut restriction by any other program. 

How t reset wastebin feature for Digikam?

thank you, Miel

---

### Post by slickymaster on 2013-01-24
It could be that it's reading Trash wrong. Try to empty trash in terminal, or cd Trash and see what's there.

```
gksu nautilus
```
Then in View select the Hidden files option so you can examine **/home/username/.local/share/Trash**

---

### Post by miel on 2013-01-26
I think that the problem is caused by some setting within Digikam. 
Because manually removing or dragging images from Digikam to the waste basked poses no difficulty. 
So it is not a serious problem but I miss the ease of simply clicking the image with the Delete key in order to move it to the waste basket.
It is a curious phenomena that i would like to set straight.  

If anyone can shed light on this challenge i will appreciate it. If not, I will muddle along for some time.
Thanks anyway for your attention,
Miel

---

