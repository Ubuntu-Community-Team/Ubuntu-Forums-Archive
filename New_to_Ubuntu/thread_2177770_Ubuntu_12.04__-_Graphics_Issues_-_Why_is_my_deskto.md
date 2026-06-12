---
title: "Ubuntu 12.04  - Graphics Issues - Why is my desktop pixelated?"
date: 2013-09-30
forum: New to Ubuntu
---

### Post by laterdaysluke on 2013-09-30
I have a HP Pavilion g7 ad am very new to Ubuntu. I finally managed to make the dual boot work with 10.04, which I then updated to 12.04 (couldnt directly install 12.04). 

Now I have 12.04 up and working, but I have a strange pixelation issue - the left part of my desktop near the launcher is pixelated and green.
Also, the fonts are not as crisp as they should be. What should I do?

The output of 
```
lspci | grep VGA
```

is

s00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Sumo [Radeon HD 6480G]

---

### Post by laterdaysluke on 2013-09-30
solved
[http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/126513#126513](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/126513#126513)

---

