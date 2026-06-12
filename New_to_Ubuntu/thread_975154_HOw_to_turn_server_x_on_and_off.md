---
title: "HOw to turn server x on and off???"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by appoloin on 2008-11-08
Hi guys,

Just intalled my new vidoe card and when i try installing the driver i get error to turn off server X..

cant remember the command please help me remember:popcorn:

---

### Post by sisco311 on 2008-11-08
```
sudo /etc/init.d/gdm stop
```and
```
sudo /etc/init.d/gdm start
```

---

### Post by bumanie on 2008-11-08
Sorry wrong post. 
Sorry, posted on the wrong thread, but I suggest that you try the hardware driver first, it usually works well. Installing video drivers the way you are proposing is OK, but come a kernel update and you will have to reinstall the drivers again. If done with hardware drivers, if there is a kernel update, the video driver will update also. I would only use the above method if hardware drivers doesn't work - a last resort type scenario.

---

### Post by drakeman007 on 2008-11-08
> **appoloin said:**
> Hi guys,

Just intalled my new vidoe card and when i try installing the driver i get error to turn off server X..

cant remember the command please help me remember:popcorn:


To restart X.
```

Ctrl + alt + backspace

```

---

### Post by glotz on 2008-11-08
Yet another way is to logout and then login.

---

### Post by aktiwers on 2008-11-08
Do like Sisco311 says.
```
sudo /etc/init.d/gdm stop
```That is what you need to do if you want to install the nvidia driver.

Then:
```
sudo chmod +x Nvidiadriverfile.bin
```

and lastly:
```
sudo ./Nvidiadriverfile.bin
```

---

