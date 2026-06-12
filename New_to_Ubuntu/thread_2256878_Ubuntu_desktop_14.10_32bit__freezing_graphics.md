---
title: "Ubuntu desktop 14.10 32bit  freezing/ graphics"
date: 2014-12-15
forum: New to Ubuntu
---

### Post by trevor20 on 2014-12-15
Hello all, I am new to the Ubuntu world and I just installed 14.10 on my desktop once it is loaded into the user's desktop screen it works fine for a few minutes then starts to lag and freeze ultimately locking up with the screen looking like it was scratched up with a wire brush. I'm not sure if it is a graphics card or processor problem the graphics card is a nvidia Geforce 6 integrated on the motherboard. Any ideas would be greatly appreciated. 

Thank you

---

### Post by sandyd on 2014-12-15
> **trevor20 said:**
> Hello all, I am new to the Ubuntu world and I just installed 14.10 on my desktop once it is loaded into the user's desktop screen it works fine for a few minutes then starts to lag and freeze ultimately locking up with the screen looking like it was scratched up with a wire brush. I'm not sure if it is a graphics card or processor problem the graphics card is a nvidia Geforce 6 integrated on the motherboard. Any ideas would be greatly appreciated. 

Thank you

The Geforce 6 card probably does not have enough power to run the Unity interface. Try a lighter distro such as Lubuntu or Xubuntu.

If the same issues occur on Lubuntu or Xubuntu, try installing the Nvidia Proprietary drivers.
Note that since you cannot access the GUI, I suggest using a wired connection to perform the installation.

To install:
[LIST=1]
[*]Press control + alt +f1
[*]Login using your username/password (password will not show up)
[*]Type the following
```

sudo apt-get update
sudo apt-get install nvidia-304
```
[/LIST]

---

### Post by trevor20 on 2014-12-16
Installed Lubuntu 14.10 and it works great thanks for the help! My machine was older then I first remembered.:P:P:P

---

