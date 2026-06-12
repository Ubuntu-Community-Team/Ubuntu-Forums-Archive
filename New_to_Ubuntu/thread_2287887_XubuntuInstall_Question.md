---
title: "Xubuntu/Install Question"
date: 2015-07-23
forum: New to Ubuntu
---

### Post by mark20clifton on 2015-07-23
So i have xubuntu 15.04 installed on my main laptop, and i have a passcode programmed on it that locks the disk (passcode not password. like numbers) i had to shutdown my laptop by holding in the power key one day because it didn't come out of standby mode properly, now i cannot enter my passcode because the part that enters your text is in the wrong spot, aka top of screen. i made a thread on this here before that wasn't answered, this time i was wondering. Is there a way i can install ubuntu on that laptop while keeping what's on my desktop and in my home folder intact? like i have stuff in documents, pictures, etc. i'm not the most computer savvy so any help is appreciated, i've heard others say even if they tell it not to overwrite the home folder it does anyway, i need to prevent that cause i do not have backups of those files. thanks

---

### Post by Bucky Ball on 2015-07-23
Installing another desktop environment or upgrading your system on a broken install has a 99% chance of not fixing the problem and a good chance of increasing chaos and confusion.

Even if you can't see the window where you enter your password, you can still enter it then hit enter. That should get you to a desktop where you can try to fix it and give us more details to help.

You can also hit control+alt+F1 and that should get you to a CLI where we can have a further poke about. You can use this method if your computer doesn't come out of standby, too. Hit that key combo, login, then:

```
sudo reboot -h now
```

... will restart the machine with a hard shutdown.

---

### Post by mark20clifton on 2015-07-23
> **Bucky Ball said:**
> Installing another desktop environment or upgrading your system on a broken install has a 99% chance of not fixing the problem and a good chance of increasing chaos and confusion.  Even if you can't see the window where you enter your password, you can still enter it then hit enter. That should get you to a desktop where you can try to fix it and give us more details to help.  You can also hit control+alt+F1 and that should get you to a CLI where we can have a further poke about. You can use this method if your computer doesn't come out of standby, too. Hit that key combo, login, then:  ```
sudo reboot -h now
```  ... will restart the machine with a hard shutdown.  The install isn't broken it worked fine till i had to do that hard shutdown, i can see the screen but it's not a password, it's a passcode i enter to unlock my disk, than get to the login screen which has a separate password. i cannot enter the passcode due to the placement of where it's entered, it's staying stuck at the top left.

---

### Post by Bucky Ball on 2015-07-23
Have you tried entering it anyway and hitting enter?

---

### Post by kerry_s on 2015-07-23
try alt+f7 to move the window into view.

---

### Post by mark20clifton on 2015-07-26
ok i tried both of those, neither worked. i just don't want to lose my files.

---

### Post by Skaperen on 2015-07-26
can you remove the disk and put a *new disk* in it (maybe bigger)?   *how big is the existing hard drive?*  does your computer have [USB 3.0]("https://en.wikipedia.org/wiki/USB_3.0") (USB sockets with blue tabs)?


*right now* i am making a backup of my computer to a [2 TB external USB 3.0 hard drive]("https://www.bhphotovideo.com/c/product/983293-REG/western_digital_wdbmwv0020bbk_nesn_2tb_my_passport_ultra.html"). a live CD ubuntu can make a backup up your data.

---

### Post by mark20clifton on 2015-07-28
> **Skaperen said:**
> can you remove the disk and put a *new disk* in it (maybe bigger)?   *how big is the existing hard drive?*  does your computer have [USB 3.0]("https://en.wikipedia.org/wiki/USB_3.0") (USB sockets with blue tabs)?   *right now* i am making a backup of my computer to a [2 TB external USB 3.0 hard drive]("https://www.bhphotovideo.com/c/product/983293-REG/western_digital_wdbmwv0020bbk_nesn_2tb_my_passport_ultra.html"). a live CD ubuntu can make a backup up your data.  Yeah no i can't, it's a laptop, and i don't have a spare disk. the usb sockets do not have blue tabs. But a sandisk cruzer works in it, along with other usb devices, i was trying to access the data by getting it put in the tmp folder but that didn't work out, says i can't access the folder due to permissions, also natilus gksu isn't even installed so i can't use that.

---

### Post by Bucky Ball on 2015-07-28
nautilus gksu? Try:

```
gksudo nautilus
```

... in a terminal.

---

### Post by sudodus on 2015-07-28
I think Xubuntu used/uses Thunar as file browser

```
gksudo thunar
```

---

### Post by Bucky Ball on 2015-07-28
> **sudodus said:**
> I think Xubuntu used/uses Thunar as file browser

```
gksudo thunar
```

Yep, it do. :)

---

### Post by mark20clifton on 2015-08-15
Ok so i'm trying to recover them using a liveiso of ubuntu, using the try it thing, none of those commands work, i can get the folder in tmp, but can't get the files cause their still encrypted. sorry for late reply been busy. Update, photo, look at the top left. [IMG]http://41.media.tumblr.com/bdd65dd1f56313b42ed6fc8c900909b7/tumblr_nt6uwyakko1sxd5azo1_1280.jpg[/IMG]

---

### Post by sudodus on 2015-08-17
Maybe this rather recent thread will help you

[How to mount encrypted /home partition with / partition is borked?](http://ubuntuforums.org/showthread.php?t=2286324)

---

