---
title: "New PC Requierments"
date: 2012-09-15
forum: New to Ubuntu
---

### Post by CurseThePhobia on 2012-09-15
Hei there guys! I just installed ma ubuntu on one of my cousin Netbook. It seem run smoothly without lag, well. Its former OS is windows 7. but my cousin ask me to chnge into new os. So i give her Ubuntu 12.04 LTS. Also, the graphic card are GMA. But, whne i tried to find it using additional driver, it cannot detect the graphic card. Is this some kind of error or it just be like that?:mad:

---

### Post by deadflowr on 2012-09-15
I'm guessing by GMA, you mean Intel GMA XXX(whatever the card number is.
Intel graphics card for linux are open-source only, and built into the kernel. No need to dig into the additional drivers looking for them. Additional Drivers lists closed source, Proprietary drivers only.
If in the details subsection in the system settings page lists the driver as unknown, simply in the package mesa-utils.

```
sudo apt-get install mesa-utils
```

Other then that, does the graphics seem okay?

---

