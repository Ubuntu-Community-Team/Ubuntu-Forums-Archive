---
title: "How to set Unity 2D as default?"
date: 2011-10-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by tjeremiah on 2011-10-07
I am aware this is a beta version of Ubuntu 11.10.

I just installed Ubuntu 11.10 on a netbook and everything is running smooth. The only problem that I've noticed is that whenever I reset the computer, Ubuntu always logs me into Ubuntu 3D even though I last left the desktop session with Ubuntu 2D.

I've set Ubuntu to log in automatically because I find it to be more convenient. How does one solve this issue?

---

### Post by lucazade on 2011-10-08
```
sudo sed -i 's/user-session=ubuntu/user-session=ubuntu-2d/g' /etc/lightdm/lightdm.conf
```

---

### Post by tjeremiah on 2011-10-08
> **lucazade said:**
> ```
sudo sed -i 's/user-session=ubuntu/user-session=ubuntu-2d/g' /etc/lightdm/lightdm.conf
```

Thank You :P

---

### Post by lucazade on 2011-10-08
you're welcome!

---

