---
title: "how do I download and use Google earth with Ubuntu"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by mtstifflers on 2008-09-03
How do I use Google Earth with Ubuntu

---

### Post by t0p on 2008-09-03
Google earth is available through synaptic and apt-get:

```
sudo apt-get install googleearth
```

---

### Post by k3lt01 on 2008-09-04
Go to Synaptic scroll down to Google Earth and select the appropriate version (there is 4.2 and 4.3) then apply changes and let it download and install. As for how to use it you use it the exactly same way as in any other Operating System.

---

### Post by Ryadt on 2008-09-04
> **mtstifflers said:**
> How do I use Google Earth with Ubuntu

You first need to add medibuntu to your repos.```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
``````
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
then install google earth```
sudo apt-get install googleearth
```

---

