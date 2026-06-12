---
title: "I can't add Handbrake in 12.04?"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by mikee55 on 2012-06-04
Why can't I get Handbrake to install on 12.04? Even Avidemux crashes every time I save a file.
Can you help please. I'm 64 bit?
Avidemux is still trying to install if I hover the mouse of the launcher, if I click on it, it opens???

Mike

---

### Post by wilee-nilee on 2012-06-04
> **mikee55 said:**
> Why can't I get Handbrake to install on 12.04? Even Avidemux crashes every time I save a file.
Can you help please. I'm 64 bit?
Avidemux is still trying to install if I hover the mouse of the launcher, if I click on it, it opens???

Mike

The link form the handbrake page is to a PPA, 12.04 is not listed in the supported downloads.

---

### Post by orange2k on 2012-06-04
You can install it using these steps:

```
sudo apt-add-repository ppa:stebbins/handbrake-snapshots
sudo apt-get update
sudo apt-get install handbrake-gtk
```

---

### Post by mikee55 on 2012-06-04
Thanks orange2k, installed and running, I thank you again :)

Mike

---

