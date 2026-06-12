---
title: "Error Wifi and camera"
date: 2024-06-01
forum: New to Ubuntu
---

### Post by juvinao95 on 2024-06-01
Hello guys, I come to ask you for help, I am new to the world of Linux, I installed Ubuntu 24.04 but I have had problems with the wifi and the camera, in the case of wifi, it connects to the network but after 5 minutes it disconnects, now I am connected by cable, and in the case of the camera I get "No camera found", my PC is a VivoBook_ASUSLaptop X415EA laptop and the Intel® Pentium® Gold 7505 × 4 processor.

---

### Post by currentshaft on 2024-06-01
What do you mean by "disconnect" from wireless? Does it work consistently for five minutes?

Where do you get "No camera found" - which application is showing errors? Does the camera show up in the output of the "lspci" command?

---

### Post by Rex Bouwense on 2024-06-02
So far I have installed 24.04 on 14 different computers and had a similar problem on one of them ("no camera found").  I offer this not as a solution but as a work-around.  Install Cheese from the repositories.  It worked for me.

---

### Post by ActionParsnip on 2024-06-03
what is the output of:
```

sudo lshw -C network; lsb_release -a; uname -a; dmesg | grep -i firm

```
Thanks

---

