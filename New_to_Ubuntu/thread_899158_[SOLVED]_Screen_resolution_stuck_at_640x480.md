---
title: "[SOLVED] Screen resolution stuck at 640x480"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by steinzeitmensch on 2008-08-24
Hi I am new to Ubuntu having only switched to it in the last 3 weeks on my Lenovo laptop.
A few days ago I had a problem that the screen would stay blank after login.
After many trials and tribulations, and with the help fo the all you great Ubuntu users, I got my screen back but it is now locked at 640x480.
In the 'Monitor resolution settings' it seems I have no other screen resolution options.
I checked other posts and tried some of the things that helped them, but so far not luck.

Can someone help me please :(

---

### Post by Flyingjester on 2008-08-24
what kind of card do you have?

---

### Post by anewguy on 2008-08-24
Please do a "lspci" in a terminal window and copy/paste the output back here.  Have you installed a driver for your video card?  Also, please copy/paste your xorg.conf file here as well.

---

### Post by Ryadt on 2008-08-24
Try ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by steinzeitmensch on 2008-08-24
> **anewguy said:**
> Please do a "lspci" in a terminal window and copy/paste the output back here.  Have you installed a driver for your video card?  Also, please copy/paste your xorg.conf file here as well.

Here they are attached

---

### Post by steinzeitmensch on 2008-08-24
> **Ryadt said:**
> Try ```
sudo dpkg-reconfigure xserver-xorg
```

Not one to give up, I ran through this command and all the questions that come up with in, and hey presto, my screen is back.

many thanks

---

