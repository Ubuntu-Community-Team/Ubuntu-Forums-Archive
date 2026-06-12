---
title: "how to get rid of edubuntu"
date: 2012-04-13
forum: New to Ubuntu
---

### Post by jjonnynitro138 on 2012-04-13
A friend of mine told me how great it was so I checked out Edubuntu by downloading through the Ubuntu software center. I don't like it :) and when I went back to the store to remove it by clicking on remove. It went through the process of removing it, but when I started up Edubuntu was still there. Even when I log out I don't have the option to use just the plain ole Ubuntu 11.10 that I like. How do I remove this OS and get mine old one back?
Thank you 
JJonnynitro138

---

### Post by daslinkard on 2012-04-13
Did you download Edubuntu along an existing Ubuntu OS?  If so, to remove the Edubuntu Desktop you will run the following command:

```
 
sudo apt-get remove edubuntu-desktop

```If you have to reinstall the gnome desktop you will do the following command:

```
sudo apt-get install --reinstall ubuntu-desktop
```

---

