---
title: "How to install Install Openshot"
date: 2021-08-12
forum: New to Ubuntu
---

### Post by aricroy on 2021-08-12
How to install Openshot in Lubuntu which extension is openshot.AppImage

---

### Post by monkeybrain20122 on 2021-08-12
Removed for double post

---

### Post by monkeybrain20122 on 2021-08-12
You don't need to install an appimage. Right click from properties > permission check allow to execute. Then you can start the app by just clicking it. An appimage is kind like a portable app.

---

### Post by coutte-chris on 2021-08-14
> **aricroy said:**
> How to install Openshot in Lubuntu which extension is openshot.AppImage

As posted above , the AppImage is a portable app , which you can execute directly. 
But the best appraoch would be the install through the official PPA, so that you can benefit from future updates automatically

to do so , open your terminal and enter the below:
```
sudo add-apt-repository ppa:openshot.developers/ppa
sudo apt-get update
sudo apt-get install openshot-qt
``` 

Source: [https://www.openshot.org/ppa/](https://www.openshot.org/ppa/)

Have fun, OpenShot is a great software.

---

