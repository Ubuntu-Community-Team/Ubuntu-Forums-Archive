---
title: "HOWTO: Install Nvidia drivers on Edgy Eft"
date: 2006-09-19
forum: Outdated Tutorials &amp; Tips
---

### Post by radiohead on 2006-09-19
Hola guys. I found that every time I installed the nvidia-glx package, X broke. So this is what I did to get it working.

```


wget http://download.nvidia.com/XFree86/Linux-x86/1.0-8774/NVIDIA-Linux-x86-1.0-8774-pkg1.run
sudo apt-get install xserver-xorg-dev

```

then I ran the installer and it compiled the new modules and now it works perfectly.

Sorry if this is in the wrong spot, I didn't see any Edgy forums.

---

### Post by juhizz on 2006-10-12
> **radiohead said:**
> 
then I ran the installer and it compiled the new modules and now it works perfectly.



How do you run the installer, I have had so many problems and i have tried so many different things, so i want to be sure how to run it?](*,)

---

### Post by ~LoKe on 2006-10-12
> **juhizz said:**
> How do you run the installer, I have had so many problems and i have tried so many different things, so i want to be sure how to run it?](*,)

```
sudo sh NV*.run
```

---

### Post by Bad_Byte on 2006-11-24
- delete my post please -

---

