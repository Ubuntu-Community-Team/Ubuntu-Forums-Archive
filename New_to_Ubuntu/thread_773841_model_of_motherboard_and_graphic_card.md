---
title: "model of motherboard and graphic card"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by nama on 2008-04-29
:KS
Hello all,
how do I find which model of Motherboard and Graphic Card is on the machine? Actually, how do I find a list of all the hardware?
For those who know windows, I need information which is given by the software like Aida 32.
Thank you.

---

### Post by SnakeHips on 2008-04-29
in terminal 

for hardware
```
lshw
```

for your graphics card
```
lspci | grep VGA
```

motherboard...i'd like to know that one myself :-)

---

### Post by owenll on 2008-04-29
```
sudo lshw -html > hardware.html
```

will create a new file called hardware.html in your home folder which will list the hardware on your computer.

---

