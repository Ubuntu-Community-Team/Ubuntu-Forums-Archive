---
title: "Help! Xubuntu 7.04 stuck at 640x480"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by m1kelang on 2008-05-22
Hi.

I'm very new to linux, and I just started using Xubuntu about a month ago. However, I found that Hardy ran quite slow, so I decided to install Feisty instead. It's a lot faster, but my screen resolution is stuck at 640x480 with no other options. How can I fix this? Any help would be greatly appreciated.

Thanks.

---

### Post by overdrank on 2008-05-22
> **m1kelang said:**
> Hi.

I'm very new to linux, and I just started using Xubuntu about a month ago. However, I found that Hardy ran quite slow, so I decided to install Feisty instead. It's a lot faster, but my screen resolution is stuck at 640x480 with no other options. How can I fix this? Any help would be greatly appreciated.

Thanks.

Hi and welcome, what is the graphics card and have you installed the drivers? You can reconfigure you xorg in the terminal with this command 
```
sudo dpkg-reconfigure xserver-xorg
```

---

