---
title: "Xfce goodies"
date: 2016-10-24
forum: New to Ubuntu
---

### Post by jshack01 on 2016-10-24
I would like to use something I found in the xfce4 goodies called xfce4-calculator-plugin and I have no idea where to begin. 

Well, that's not completely true, I downloaded the latest release and completed './configure' and 'make' and 'make install' [seemingly correctly] but I gots nothing. Are these tools incompatible with Ubuntu? I am running 14.04.

---

### Post by cariboo on 2016-10-24
The xfce4-goodies are in the repository, no need to compile the package yourself:

```
sudo apt-get install xfce4-goodies
```

---

### Post by Dennis N on 2016-10-24
I would think a panel plugin is not going to be any better than the existing available calculators - some have advanced scientific and financial modes. The current xfce4-goodies package (4.12.1) in the Xenial repository doesn't include any calculator plugin. The plugins are for the xfce4 environment, so unless you have xfce4 installed, or use Xubuntu, I would suspect you can't use them.

---

