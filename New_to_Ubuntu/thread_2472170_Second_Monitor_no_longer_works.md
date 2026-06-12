---
title: "Second Monitor no longer works"
date: 2022-02-19
forum: New to Ubuntu
---

### Post by philly1ms on 2022-02-19
My second monitor stopped working after updating Ubuntu.  Any suggestions to look at?  It was working fine on the latest NVIDIA drivers but  after doing a UBUNTU update it won't display.  I can get dual display using the laptop screen and 1 external monitor.  

NVIDA Version 510.47.03
UBUNTU version 20.04.4 LTS Focal
Kernel 5.13.0-30

Thank you

---

### Post by MAFoElffen on 2022-02-19
Start up NVidia Settings and see if it sees the second display. If not, in order, go Ubuntu's Activities > Type "Display"... The Terminal
```

xrandr -q

```
It sounds like a setting just got changed.

---

### Post by philly1ms on 2022-02-19
> **MAFoElffen said:**
> Start up NVidia Settings and see if it sees the second display. If not, in order, go Ubuntu's Activities > Type "Display"... The Terminal
```

xrandr -q

```
It sounds like a setting just got changed.
  
Thanks for the reply.  I booted into Windows and it wasn't working there. Moved cables around to make sure monitor was working and now both are working in Ubuntu.  Not sure what made it start working again but it is.  Thanks again.

---

### Post by MAFoElffen on 2022-02-19
Happy it is working now.

Please remember to use the Thread Tools in the upper right of this page to mark this as Solved, so other can find what worked for you, to solve their similar problems.,

---

