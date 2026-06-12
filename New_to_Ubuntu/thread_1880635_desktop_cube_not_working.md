---
title: "desktop cube not working"
date: 2011-11-14
forum: New to Ubuntu
---

### Post by kishore328 on 2011-11-14
hi frnds

am using ubuntu 11.10 in this in compiz config manager ubuntu utility package is missing how to download that package,,,,,,,:):):)

---

### Post by bokgeneraal on 2011-11-14
Search for compiz in software centre , install "CompizConfig Settings Manager".I tried getting the cube to work by installing "ccsm" and configuring it. It did not work for me. The cube does still work under KDE's KWIN ( install kubuntu-desktop ).:D

---

### Post by tushar maroo on 2011-11-14
as you are working on latest edition of ubuntu,it have a unity package set as default,if you want to get back to facilities like 3d-cude  and wobbling windows then you have to remove unity package ,but before install compiz form command line 
sudo apt-get install compizconfig-settings-manager
then hit enter you will be able to install compiz then you can set your needs in manager.

---

### Post by grahammechanical on 2011-11-14
I have a working wobbly windows effect on 11.10 + Unity 3D. I have not tried any of the other effects. Some have reported issues with some of these other effects. Be careful! Make sure you can load into 2D to reverse anything you try. Make sure you know how to get into a terminal to run the shutdown command. It might be the only way (apart from the computer on/off switch) of shutting down for a reboot.

Compiz is installed by default as it is the compositing window manager for Unity. It is CompizConfigurationSettingsManager (CCSM) that has to be installed if you want to have desktop effects including changing Unity 3D settings.

Do not assume that all the compiz settings options will work and not break the desktop.

Regards.

---

### Post by Frogs Hair on 2011-11-14
Search for guides for enabling the cube in _11.10_ I found a few with a search . I managed to get the cube working the first try on installation day and have left The CCSM alone since except for the Unity Plug-in . Some guides include commands if you run into problems.

---

