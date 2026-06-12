---
title: "Cannot install ATI Radeon 9250 Drivers: Unable to detect X Server."
date: 2008-06-27
forum: New to Ubuntu
---

### Post by Mortel on 2008-06-27
Alright, I am very new to Linux (just installed Ubuntu 8.04 for the first time yesterday) and I think I need to install the drivers for my video card.  I am running a Dell Dimension with a ATI Radeon 9250 (please ignore the age of my computer and graphics card, it's all that I have).

Anyways, here is the driver I am trying to install:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.28.8.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.28.8.run)

I save it to the desktop, and hit Control + Alt + F1, and type:

```
/etc/init.d stop
cd Desktop
sudo sh ati-driver-installer-8.28.8.run
```

It then goes to work, and I get this error message:
```
Detected Configuration:
Architecture: i686 (32 bit)
X Server: unable to detect
Removing temporary directory: fglrx-install
```

Any help would be greatly appreciated.

---

### Post by ajgreeny on 2008-06-27
I think thr open source driver that was installed when you installed the system works well with that card, it certainly does with my 9200se card.

---

### Post by sheds on 2008-07-01
My installation did not install anything. Usually, i get some kind of message letting me know that restricted drivers are already being used, or in any case, the possibility of using them for the card i have. My problem is that my computer does not seem to find my video card. Its an ati 9200 SE, just like yours; I went to the ati site and found the drivers, but i get the same issue as the thread starter.

I tried using the fglrx option but i cannot find a xorg.conf file that matches what i have.

What would be the next step in the attempt to install the drivers???

---

### Post by zerobinary on 2008-07-01
I don't think you need to install the driver.
I used to use ati 9200 and it doesn't requires a driver.
But anyway this is the way you should do it.
I think the problem for you is you don't have the right compiler.
[code]
sudo -i 
sudo apt-get install build-essential 
cd the directory
ati-driver-installer-8.28.8.run

---

