---
title: "Checking computer specification on a live box"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by Tsu on 2008-11-12
Hi Everyone,

How do you check a server on the console for different hardware specifications?

Example. Ifconfig gives me the ip address and MAC address.

How do I get an output of total RAM? How big the hard drive is and the usage. Speed of the CPU and the make and model of the graphics card. Also the model of the motherboard. Is any of this accessible from the terminal console?

---

### Post by jimmy the saint on 2008-11-12
```
lshw
```

---

### Post by Elfy on 2008-11-12
```
sudo fdisk -l
df -h
free -m
sudo lshw | less
```

should give you that information

---

### Post by Tsu on 2008-11-13
wow, this info is really helpful. especially the df. reading the man files for more detailed info. Keep em coming thanks

---

