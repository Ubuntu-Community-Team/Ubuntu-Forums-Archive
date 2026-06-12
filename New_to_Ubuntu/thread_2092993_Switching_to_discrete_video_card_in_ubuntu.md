---
title: "Switching to discrete video card in ubuntu"
date: 2012-12-09
forum: New to Ubuntu
---

### Post by Athquiz on 2012-12-09
I have a lenovo laptop, Y580, with a 64-bit 12.04 ubuntu installation. I'm trying to access my NVIDIA video card to run some 3D games, but I don't seem to be able to use it. I've downloaded bumblebee, but it doesn't seem to work. Trying to run anything with optirun gives me this error message:
```
[ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.
```

lspci | grep VGA finds both video cards. Additional drivers says that nvidia-common is "activated, but currently not in use."

I've been googling furiously to find a solution, but they either don't work or are beyond my abilities. I was wondering if someone here could help.

---

### Post by Athquiz on 2012-12-13
Well I've solved this problem. There was a hack to get bumblebee working on my laptop. In case anyone else has the same problem as me go [here.]("http://chrislaidler.blogspot.ca/2012/12/getting-nvidia-optimus-working-on-my.html")

---

