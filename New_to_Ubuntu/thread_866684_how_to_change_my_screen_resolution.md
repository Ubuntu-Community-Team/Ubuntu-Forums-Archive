---
title: "how to change my screen resolution ?"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by Dileeshvar on 2008-07-22
hello there guys 
i have just now bought my new system and have installed Ubuntu 8.04.
the problem that am facing now is that i am not able to change my screen 
resolution from 800X600 to 1024X768 I use an inbuilt NVIDA graphic card with the motherboard.please someone help me !!
am an absolute beginner so suggest me some easy steps !!:(:mad:

---

### Post by iaculallad on 2008-07-22
> **Dileeshvar said:**
> hello there guys 
i have just now bought my new system and have installed Ubuntu 8.04.
the problem that am facing now is that i am not able to change my screen 
resolution from 800X600 to 1024X768 I use an inbuilt NVIDA graphic card with the motherboard.please someone help me !!
am an absolute beginner so suggest me some easy steps !!:(:mad:

Try to use:

```
sudo nvidia-settings
```

or

```
sudo nvidia-xconfig
```

---

### Post by Dark_Stang on 2008-07-22
Make sure you've got the nvidia driver installed. 
Go System > Administration > Hardware Drivers. And make sure it's installed and running. If it isn't, check the box and it will have you reboot. It normally autodetects at this point and adjusts itself. If it doesn't I suggest installing the nvidia x server settings manager. You can make all your adjustments through that.

---

