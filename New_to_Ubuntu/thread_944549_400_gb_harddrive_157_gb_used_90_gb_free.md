---
title: "400 gb harddrive 157 gb used 90 gb free"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by SpenceMakesSense on 2008-10-11
On my linux harddrive i had deleted everything but my home directory to make it a seperate home partition. Well after all of that it says my hardrive has only 90 gb free and its using 290 gb while the harddrive is only 157 gbs used. Im very confused and need some help

---

### Post by linux6994 on 2008-10-11
Have you emptied the trash?

---

### Post by SpenceMakesSense on 2008-10-11
yes i made sure and I viewed the hidden files and all that is there is the home directory.

---

### Post by SpenceMakesSense on 2008-10-12
bump

---

### Post by ratmandall on 2008-10-12
Is ubuntu the only os on your hardrive?

---

### Post by howlingmadhowie on 2008-10-12
can you post the results of ```
df -h
``` and ```
cat /proc/partitions
```?

---

### Post by SpenceMakesSense on 2008-10-13
Wait I found it. Theres a folder called .local that was taking up n extra 79 gb. After investigating it had  a seperate trash folder that had saved every little thing i had ever deleted. 
after deleting it it still said i had 157 gb used but 160 gb free. I know that still doest add up but im sure the rest of the space is taken up in those hidden folders. I figured it would have calculated those in

---

