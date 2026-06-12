---
title: "Drivers"
date: 2013-02-15
forum: New to Ubuntu
---

### Post by Zeyo on 2013-02-15
Well... I am here for really short time and I am an absolute newbie to Linux who just installed it... So sorry if I placed this thread in wrong place :|

Anyway, I have some problems with drivers... I'd like to install drivers for my Graphic card... however I didn't find them anywhere. I tried using the disc that came with the card (which was... dumb).

And second thing I'd like to ask about... I don't know is it connected to this, but I sometimes get black screen when I boot and re-plugging my VGA cable seems to temporary solve the issue.

Any suggestions what I could do?

Oh yeah, I use Ubuntu 12.10 and my full PC spec is:

Intel i3 3.3GHz 2120
Asus P8 H61 M LE motherboard
Asus HD6670 (1GB GDDR3)
Kingston 4GB DDR3 RAM

Thanks :)

---

### Post by omeomi on 2013-02-15
You can install the proprietary drivers by using the Additional Drivers. In your Ubuntu version you can find this in Software Sources (just use Dash to search for that) and than the last tab should be the drivers.

---

### Post by Perfect Storm on 2013-02-15
If you're looking for gaming you might look into restricted driver for your card. But by default your card is supported out of the box.

Checking for restricted drivers:
1. click Super key (the window key)
2. write 'driver'
3. click it and check if there're any available driver.

---

### Post by Zeyo on 2013-02-15
> **omeomi said:**
> You can install the proprietary drivers by using the Additional Drivers. In your Ubuntu version you can find this in Software Sources (just use Dash to search for that) and than the last tab should be the drivers.

Tried this... A second ago and I'll see what will happen...

> **Artificial Intelligence said:**
> If you're looking for gaming you might look into restricted driver for your card. But by default your card is supported out of the box.

Checking for restricted drivers:
1. click Super key (the window key)
2. write 'driver'
3. click it and check if there're any available driver.

No drivers displayed in the "dash" :/
And yeah, gaming is one of my interests. At the moment, Steam and Java are my only gaming sources...

---

### Post by Perfect Storm on 2013-02-15
No 'Additional Drivers' icon?

EDIT: also if you want to use steam read this: [https://wiki.ubuntu.com/Valve#AMD.2BAC8-ATI_Graphics](https://wiki.ubuntu.com/Valve#AMD.2BAC8-ATI_Graphics)

---

### Post by dennisjj4 on 2013-02-15
Well, it look like that 'ASUS HD6670' is your video card. That is a ATi/AMD Radeon GPU, and you need to go to the 'Additional Drivers' section in the system settings to install your drivers. The driver you will need is (most likely) fglrx.

---

### Post by Zeyo on 2013-02-15
> **Artificial Intelligence said:**
> No 'Additional Drivers' icon?

EDIT: also if you want to use steam read this: [https://wiki.ubuntu.com/Valve#AMD.2BAC8-ATI_Graphics](https://wiki.ubuntu.com/Valve#AMD.2BAC8-ATI_Graphics)

The first person who posted here after me told me to do this and I did it... Now System Setting > Details > Graphics still say "Unknown driver". And no Additional drivers icon in dash, but in Software sources.

And a bit clumsy question. I don't understand these:
Update your repository to the latest version in the Update Manager.
Remove the currently installed drivers.

EDIT:
Steam won't work anymore. Running it in terminal outputs:
```

zeid@P8-H61:~$ steam
Running Steam on ubuntu 12.10 32-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1360841030_client)
SteamUpdateUI: An X Error occurred
X Error of failed request:  BadAlloc (insufficient resources for operation)

```

---

### Post by Zeyo on 2013-02-15
I solved it. Thanks for your support.

I just followed some terminal commands from  [https://wiki.ubuntu.com/Valve#AMD.2BAC8-ATI_Graphics](https://wiki.ubuntu.com/Valve#AMD.2BAC8-ATI_Graphics)

---

