---
title: "Ubuntu screen messed up"
date: 2013-08-24
forum: New to Ubuntu
---

### Post by cole3 on 2013-08-24
Hi I just installed Ubuntu 13.04 on my Compaq Presario v6500. The screen is messed up. There are 3 sections on the screen going up and down that show the same thing. I have it connected to an external monitor right now. Any idea how I can fix this? Also, how can I get Wifi working?

---

### Post by Impavidus on 2013-08-24
You need some drivers. Look for "additional drivers" or "additional hardware" somewhere in the settings of your computer (the exact name and place varies with version and flavour) and see whether the menu offers you something to install. You'll need a wired internet connection to download the drivers.

If you can't fix it, it may help if we know the exact type of graphics and wifi card in your computer. If you don't know, open a terminal and run the command```
lspci
```It will give a list of hardware present in your computer. You can post the list here.

---

### Post by cole3 on 2013-08-24
> **Impavidus said:**
> You need some drivers. Look for "additional drivers" or "additional hardware" somewhere in the settings of your computer (the exact name and place varies with version and flavour) and see whether the menu offers you something to install. You'll need a wired internet connection to download the drivers.

If you can't fix it, it may help if we know the exact type of graphics and wifi card in your computer. If you don't know, open a terminal and run the command```
lspci
```It will give a list of hardware present in your computer. You can post the list here.

Thanks for the reply. I will try this out later and let you know how it goes. I do know that my graphics card is a Nvidia GeForce 7150M/630 and my wifi card is a Broadcam 4321AG. Thanks again!

---

### Post by cole3 on 2013-08-24
> **Impavidus said:**
> You need some drivers. Look for "additional drivers" or "additional hardware" somewhere in the settings of your computer (the exact name and place varies with version and flavour) and see whether the menu offers you something to install. You'll need a wired internet connection to download the drivers.

If you can't fix it, it may help if we know the exact type of graphics and wifi card in your computer. If you don't know, open a terminal and run the command```
lspci
```It will give a list of hardware present in your computer. You can post the list here.

I couldn't find an option in Ubuntu to download a driver. Anyone else that might be able to help?

---

### Post by deadflowr on 2013-08-24
Do you not have an internet connection?
Additional Drivers need to download the drivers from the web, so until you can get a connection, it won't work.

This should get you your wifi up and running, maybe
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

I would look in the no internet access section.

Good Luck.

---

