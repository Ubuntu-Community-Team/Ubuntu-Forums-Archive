---
title: "kernel upgrade - will I lose my 66.29 drivers?"
date: 2005-02-08
forum: Repositories &amp; Backports
---

### Post by sharkzf6 on 2005-02-08
Here's a stupid question from a newb. If I change my kernel from -386 to -686 (since I have a P4), will the nVidia 66.29 drivers I installed be lost? In other words, will I have to reinstall the 66.29 package? Thanks.

---

### Post by Razvan on 2005-02-08
no you dont have to reinstall those, but you'll have to install the restricted-modules package that belongs to your new kernel in order for them to work

cheers, Martin

---

### Post by sharkzf6 on 2005-02-08
[QUOTE=Razvan]no you dont have to reinstall those, but you'll have to install the restricted-modules package that belongs to your new kernel in order for them to work

cheers, Martin[/QUOTE]
OK, so I marked the Linux-686 kernel for install in synaptic, it also marked Linux-Image-686, Linux-Image-2.6.10.-3-686 and the 2 appropriate restricted modules you mentioned, that sound right to you? Thanks.

---

### Post by sharkzf6 on 2005-02-08
Great! I did it, it worked. Thanks :D

---

