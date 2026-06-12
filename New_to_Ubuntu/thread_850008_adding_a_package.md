---
title: "adding a package"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by dtommy79 on 2008-07-05
Hi,

How can I add a package to ubuntu?
I mean my computer where the linux resides isn't connected to the internet. if I download a programe from another computer where doI have to copy the package on ubuntu and how to install it?

Thanks

---

### Post by Nikitas350 on 2008-07-05
If it is a .deb double click it and the&#957; click install. (You can download ubuntu packages from packages.ubuntu.com)

---

### Post by iaculallad on 2008-07-05
Or doing the Terminal way of installing DEB files:

Change directory to the package location and perform the following command:

```
sudo dpkg -i package_name.deb
```

To Remove the package:

```
sudo dpkg -r package_name.deb
```

---

### Post by dtommy79 on 2008-07-05
Thank you guys

---

