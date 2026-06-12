---
title: "Ubuntu  can't access web, all other partitions are fine"
date: 2011-12-11
forum: New to Ubuntu
---

### Post by thaumielx72 on 2011-12-11
Xubuntu, Kubuntu, even Windows is having no problems.  But My Ubuntu partition is telling me there is no internet connection.

Surely one of you knows the answer....

---

### Post by illgetit on 2011-12-11
From the Ubuntu partition, please post the output of the following command
```
iwlist -scan
```

---

### Post by BC59 on 2011-12-11
> **thaumielx72 said:**
> Xubuntu, Kubuntu, even Windows is having no problems.  But My Ubuntu partition is telling me there is no internet connection.

Surely one of you knows the answer....

Try to do this:
```
sudo apt-get remove network-manager
sudo apt-get install wicd
```

If the trick is not working reinstall network manager

```
sudo apt-get install network-manager
```

> @illgetit, iwlist -scan is not a correct command

---

### Post by illgetit on 2011-12-11
Yep, you're right. Should be 
```
iwlist scan
```
My bad.

---

### Post by linuxman94 on 2011-12-11
Could you post outputs of these commands? 

```
sudo lshw -C network
lsmod
iwconfig
```

---

