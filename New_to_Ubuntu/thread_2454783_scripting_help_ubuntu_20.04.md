---
title: "scripting help ubuntu 20.04"
date: 2020-12-05
forum: New to Ubuntu
---

### Post by rburkartjo on 2020-12-05
okay i am overlooking something
if i run clamscan -r -l /home/ray/clamscan.log /usr/bin
in terminal it does not save output
tks

---

### Post by SeijiSensei on 2020-12-05
I've not used the -l option, but this worked for me:
```
clamscan -r  --stdout /usr/bin > /home/ray/clamscan.log
```

---

### Post by rburkartjo on 2020-12-06
tks se
works great

---

