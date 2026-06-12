---
title: "Nvidia Linux drivers on their site ?!"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by howitz on 2008-09-17
Ok guys i have Geforce 8400 GS , now i have ubuntu gutsy gibons , i have the NVIDIA restricted drivers checked in administration but something isn't working like it should to be , almost every time things are slow , slow minimize , few opened application and it starts to choke , i think that the drivers are the main problem here.

What about installing those on nvidia site for linux , does they function on ubuntu ? And yeah , how to install them since everything it's not simple ?
Thanks forward

---

### Post by alienexplorers on 2008-09-17
I use envyng to install my drivers and I have had no problems using it.  It is available in the repositories.

---

### Post by WRDN on 2008-09-17
For easy installation of ATI/ Nvidia drivers, use EnvyNG which is available in the repositories. This will automatically detect the GPU and download/ install the appropriate driver for it.

---

### Post by Bucky Ball on 2008-09-17
Have you installed nvidia-glx-new from Synaptic Package Manager and nvidia-settings to tweak the card? Here is more info on getting the card operational:

[http://ubuntuforums.org/showthread.php?t=880787&highlight=ENVYNG](http://ubuntuforums.org/showthread.php?t=880787&highlight=ENVYNG)

---

### Post by howitz on 2008-09-17
I also use envy to install the drivers , but the problem seems to be persistent. It's slow and my PC hardware it's not that old.

@ Bucky i haven't checked that but i am going to right now...

---

### Post by tangibleorange on 2008-09-17
to install envy:

```
sudo apt-get install envyng-gtk
```

---

### Post by howitz on 2008-09-17
Bucky i have installed envy installed the nvidia drivers , i opened synaptic it's all checked except nvidia-settings , but when i check that it unmarks nvidia-glx new  :/

It's like working in windows without drivers for video , sucks big time , don't know what's the problem.

---

### Post by ru7hl3ss on 2008-09-17
Other was is:
Drop to a virtual terminal (Ctrl+Alt+F1)
```
sudo apt-get install build-essential
```
Browse to directly where you have the nvidia driver and install
```

cd /directory/where/you/have/drivers
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-whatever-the-build-is

```
Follow the on screen steps...

Then a quick 
```

sudo /etc/init.d/gdm restart
```

Should be good to go...

---

### Post by Bucky Ball on 2008-09-17
Ya see, I have never used envy, so not sure if you can use both at once (might cause a conflict as envyNG will force the driver it selects rather than the one you do perhaps). Maybe you could try removing envy, then try selecting the driver manually (nvidia-glx, nvidia-glx-new, or nvidia-legacy depending on your card) and see if that makes a difference.

Or, if envyNG is installed and it has installed the appropriate driver, install nvidia-settings so you can tweak the cards settings.

:)

---

### Post by howitz on 2008-09-17
Thanks Bucky i'll try to remove envy and select the drivers from synaptic , ill be posting soon with the results. :)

---

