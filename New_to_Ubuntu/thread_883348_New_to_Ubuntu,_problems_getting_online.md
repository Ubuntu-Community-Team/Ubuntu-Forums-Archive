---
title: "New to Ubuntu, problems getting online"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by junkmanSP on 2008-08-07
I just installed the latest version of Ubuntu on my desktop.  The first problem I am having is that I cannot use my monitor's full resolution(it is stuck on 800 x 640 or so), I believe this will be rectified by downloading the right drivers, which brings me to problem number two.

I can't get online.  Before installing ubuntu, I used a wusb54gsc adaptor.  I read up on ndiswrapper, and tried to use it to get online, but so far, I cannot get it installed, nothing I'm trying is working.

I get errors when I follow the instructions found on this forum.  What should I do?

---

### Post by tuxxy on 2008-08-07
[https://help.ubuntu.com/8.04/internet/C/index.html](https://help.ubuntu.com/8.04/internet/C/index.html)

---

### Post by st33med on 2008-08-07
Hello. What graphics card are you using? To find out, do this in the terminal:
```
lspci | grep VGA
```

---

### Post by junkmanSP on 2008-08-07
My graphics card is
"nvidia corporation C51 [GeForce 6150] (reva2)"

I get an error when I try to install ndiswrapper as per the instructions provided here.  When I do the first "make" and "make install" commands, it seems to start off OK, but ends in a bunch of warnings and errors(it ends with "error 2")  What could I be doing wrong?

---

### Post by aimpau on 2008-08-07
OUch. You've probably downloaded the source. Better go to synaptics for your download needs.

---

