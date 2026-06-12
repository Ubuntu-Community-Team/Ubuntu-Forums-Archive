---
title: "[SOLVED] how to run synaptic pakage manager in terminal"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by fr.theo on 2008-10-03
does any one know how to run the synaptic package manger in terminal?

---

### Post by nothingspecial on 2008-10-03
synaptic is a front end to apt isn`t it?

---

### Post by fr.theo on 2008-10-03
yes but it is possible to run it form terminal especially if it wont run from the system menu.

---

### Post by Elfy on 2008-10-03
You can start synaptic from the terminal ```
gksudo nautilus
```

But to install/remove from a terminal use aptitude or apt-get

```
sudo apt-get install package
sudo apt-get remove package
```

You can use aptitude in the same way or start it with

```
sudo aptitude
```
which will open in interactive mode

[https://help.ubuntu.com/community/AptitudeSurvivalGuide](https://help.ubuntu.com/community/AptitudeSurvivalGuide)

---

### Post by Sycron on 2008-10-03
If you wish to just run synaptic open up a terminal an type```
gksudo synaptic &
```

---

### Post by nothingspecial on 2008-10-03
Second half of the page

[https://help.ubuntu.com/7.04/add-applications/C/advanced.html](https://help.ubuntu.com/7.04/add-applications/C/advanced.html)

---

### Post by fr.theo on 2008-10-03
thanks it worked.

---

### Post by Sycron on 2008-10-03
You're welcome.

---

