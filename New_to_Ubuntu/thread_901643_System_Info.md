---
title: "System Info ?"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by Drakkor on 2008-08-26
Yeah, is there a program where I can find the serial # of my computer ? 
Thanks :)

---

### Post by Sbarton on 2008-08-26
Maybe try sysinfo!I believe it is in Synaptic Package  Manager.
regards

---

### Post by Vivaldi Gloria on 2008-08-26
> **Drakkor said:**
> Yeah, is there a program where I can find the serial # of my computer ? 

What do you mean by serial number? What kind of computer do you have?

---

### Post by jerome1232 on 2008-08-26
Try looking on the case, googling any numbers you find there. I've seen sudo lshw show serial numbers sometimes, it's already installed.

```
sudo lshw
```

---

### Post by ibuclaw on 2008-08-26
lshw tends to splash out way too much info on screen, so it is good to store it into a file
```
sudo lshw -html > ~/Desktop/hardware.html
```
And look on your Desktop for the output.

Regards
Iain

---

