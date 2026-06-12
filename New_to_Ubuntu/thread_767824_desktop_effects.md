---
title: "desktop effects"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by falonyn on 2008-04-25
Okay, I just installed Kubuntu on my brother's desktop computer, and this is my first time with Kubuntu. I was wondering how to get the desktop effects working. I have enabled then, installed the right stuff, and even installed the drivers for Nvidia through the package manager. I am wondering what it is I am doign wrong. I click on the button to turn them on, click apply, and then nothing happens. 

Can someone please give me a 'howto'? They are easy in Ubuntu, but in Kubuntu I am a little lost. 
Thanks.

---

### Post by Rocket2DMn on 2008-04-26
falonyn, please post the terminal output of
```
lspci | grep VGA
compiz --replace
```
For later, you can install this program to configure CF:
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by falonyn on 2008-04-26
lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)

I went in last night through the package manager and installed the nVidia 'legacy' drivers, but I am not totally sure that they are the ones that I need or that they are working properly.

---

### Post by Rocket2DMn on 2008-04-26
Those may not be the drivers you want, so let's uninistall them and have Envy find the correct drivers for you.
```
sudo apt-get remove nvidia-glx-legacy
sudo apt-get install envyng-gtk
```
If Envy doesn't run immediately, you can access it from Application->System Tools->EnvyNG
From Envy you can install the nvidia driver through automatic detection, and it will fetch the driver, download it, and install it for you.

---

