---
title: "Not utilizing proprietary drivers"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by Me887799 on 2008-07-19
[http://i35.tinypic.com/1zmzb54.png](http://i35.tinypic.com/1zmzb54.png)

I'm using an NVIDIA Geforce 8600GT, and this just happened recently.

I have used the drivers EnvyNG gives me, and the ones found on the nvidia site.

Because it is not utilizing my drivers (Or even finding them) I cannot use things like compiz ( II get "The composite extension is not available" when trying to turn the visual effects to "Extra")
I've already tried changing disabled to enabled for the compiosite device in xorg.

I am using the xorg server given to me by Envy, and I've used the xorg server given to me by using nvidia-xconfig.

---

### Post by pavel989 on 2008-07-19
remove mesa?

---

### Post by Canis familiaris on 2008-07-19
Could you post the output of:
```
lspci | grep VGA
```

---

### Post by Me887799 on 2008-07-19
> **Anurag_panda said:**
> Could you post the output of:
```
lspci | grep VGA
```

02:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)

---

### Post by Canis familiaris on 2008-07-19
> **Me887799 said:**
> 02:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
Install the nVidia drivers:
```
sudo apt-get install nvidia-glx
```
Set up the driver:
```
sudo nvidia-xconfig
```

Did this help?

---

### Post by Me887799 on 2008-07-19
> **Anurag_panda said:**
> Install the nVidia drivers:
```
sudo apt-get install nvidia-glx
```
Set up the driver:
```
sudo nvidia-xconfig
```

Did this help?

No sir.  Actually it messed up my xorg so bad I had to use xfix =/

---

