---
title: "installation"
date: 2012-03-08
forum: New to Ubuntu
---

### Post by infoglobe on 2012-03-08
how to install .tar.gz file which does'n have /configure or make install files......?

---

### Post by jerome1232 on 2012-03-08
What does it have in there? Where did you get it? Is there some documentation in there? (a README, or something similiar, perhaps a doc folder?)

Remember tar.gz files are just like zip files on windows, anything can be in there so you have to give us more info.

---

### Post by infoglobe on 2012-03-08
i m downloading WICD from [https://launchpad.net/wicd/+download](https://launchpad.net/wicd/+download) .....i am extracted it....but it d'nt containn configure file......then how i will install it

---

### Post by winh8r on 2012-03-08
You can install it from the software centre or using :

```
sudo apt-get install wicd-daemon
```

hope this helps you.

---

### Post by cortman on 2012-03-08
Extract the contents of the .tar.gz. Extract the .tar file from the contents. In there is a file called INSTALL, which will step you through installation.

---

