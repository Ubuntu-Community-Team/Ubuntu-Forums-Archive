---
title: "How to check for PVR card"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by jasontu on 2008-08-04
I recently purchased a Hauppauge PVR 150 card and I want to set it up with Mythbuntu.  I am having issues setting up Mythbuntu, but first I want to check my system even detects the card.  How could I do that?

---

### Post by benfindlay on 2008-08-04
Launch a terminal and type ```
lspci
```
Look for any reference to your hardware in that list.

Also, it is worth checking the /dev folder for the presence of a video device, named videoX (x being a number)

Hope this helps!

---

