---
title: "wireless adapter not recoganized wirless networks"
date: 2012-09-14
forum: New to Ubuntu
---

### Post by prakaz25 on 2012-09-14
Hi friends..
 i am using ubuntu 12.04...i had trouble with wirless net works.. it cant recoganized any wirless networks..
please help how can i connect the wirless networks...in ubuntu

---

### Post by blade4 on 2012-09-14
Which Wireless card are you using ? If you don't know you can find out by typing 
"lshw -C network" in terminal (minus quotes) and reading the entry marked Network controller .

---

### Post by Bucky Ball on 2012-09-14
Better still, run the command given above, adding sudo, and post the output back here, please. Just copy and paste this into a terminal: 

```
sudo lshw -C network
```

---

