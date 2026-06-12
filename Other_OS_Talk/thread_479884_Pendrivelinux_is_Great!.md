---
title: "Pendrivelinux is Great!"
date: 2007-06-20
forum: Other OS Talk
---

### Post by init1 on 2007-06-20
I tried Pendrivelinux today and it is really useful. The installation was very easy. [http://www.pendrivelinux.com/2007/05/16/usb-pendrivelinux-install-tutorial/#more-219]("http://www.pendrivelinux.com/2007/05/16/usb-pendrivelinux-install-tutorial/#more-219")

---

### Post by mr.farenheit on 2007-06-20
pretty nifty. might have to give it a try as well. never know when something like that might come in handy

---

### Post by init1 on 2007-06-21
The only problem is that booting up and shutting down is slow. The persistent live feature is nice because it saves your changes. Slax is a lot faster, but this is debian based, and I can actually use internet on it.

---

### Post by smoker on 2007-06-21
> **init1 said:**
> The only problem is that booting up and shutting down is slow. The persistent live feature is nice because it saves your changes. Slax is a lot faster, but this is debian based, and I can actually use internet on it.

try the DSL (damn small linux) usb install : [http://www.pendrivelinux.com/2007/01/02/all-in-one-usb-dsl](http://www.pendrivelinux.com/2007/01/02/all-in-one-usb-dsl)

it should boot a lot quicker. personally i have puppy linux on a flash drive (puppy has it's own installer for this), and it will boot in less than a minute.

---

### Post by init1 on 2007-06-21
Puppy Linux? I tried to install it on my usb drive, but I couldn't. There are so many options to choose, what worked for you?
For the DSL install, I don't have windows. Should I just use wine? The debain package for syslinux does not work, it complains that it does not have mcopy.

---

### Post by smoker on 2007-06-21
hi, for dsl, i can't remember off hand, (though it wasn't through wine), it was that long ago, and i replaced it with puppy and have had puppy on the flash drive for a long time now.

puppy was an easy install, i formatted the flash drive fat16, then booted from the puppy live-cd, once booted, right click screen for menu, and choose the installer, there is an option there to install to your flash drive, which it should have detected. then it is just a case of following instructions, the last of which, if i remember right, is to choose one of several possible boot methods. i think i had to try two or three of these before i could get the pc to boot from the usb. but once it is set, that is it.

hope this helps

probably better info at this link! [http://puppyos.com/flash-puppy.htm](http://puppyos.com/flash-puppy.htm)

---

### Post by smoker on 2007-06-21
here are some links for DSL install to a flash drive, i can't honestly remember if i used one of these methods, but hopefully one will work for you:
[http://www.damnsmalllinux.org/wiki/index.php/USB_Booting](http://www.damnsmalllinux.org/wiki/index.php/USB_Booting)

[http://www.damnsmalllinux.org/wiki/index.php/Installing_to_a_USB_Flash_Drive](http://www.damnsmalllinux.org/wiki/index.php/Installing_to_a_USB_Flash_Drive)

---

### Post by init1 on 2007-06-21
Thanks! I even found a link to these forums on Wikipedia for a Kubuntu persistent live installation. It's for windows, but I guess I can figure it out. I found some syslinux binaries, so I guess I will try Ubuntu next. I am actually considering using the PenDriveLinux as my main OS since I can use it on multiple computers. The Live Persistence and Debian repositories make up for the speed issues.  
[http://ubuntuforums.org/showpost.php?p=1062799&postcount=100]("http://ubuntuforums.org/showpost.php?p=1062799&postcount=100")
[http://en.wikipedia.org/wiki/Live_USB]("http://en.wikipedia.org/wiki/Live_USB")

---

### Post by init1 on 2007-06-22
I got Ubuntu to run on a USB drive! Live persistence is great!

---

### Post by Cet on 2007-10-14
> **init1 said:**
> I got Ubuntu to run on a USB drive! Live persistence is great!

Just one question: Is it also possible to install Ubuntu from live-persitence like you can do it with a live-CD? Or can you just operate Ubuntu from live-persistence?

---

### Post by init1 on 2007-10-15
> **Cet said:**
> Just one question: Is it also possible to install Ubuntu from live-persitence like you can do it with a live-CD? Or can you just operate Ubuntu from live-persistence?
I think you can. I have not tried it, but the installer icon is still on the desktop. If it does work, you could run it from live persistence or just plain live.

---

### Post by smartboyathome on 2007-10-16
I might try this with Xubuntu. Never know when it might come in handy. :)

---

### Post by Cet on 2007-10-17
> **init1 said:**
> I think you can. I have not tried it, but the installer icon is still on the desktop. If it does work, you could run it from live persistence or just plain live.
No, the question was not live persistence or plain live (btw, whats the difference?) but live persistence or install it, while you use it, like the CD.
If I would see such an USB-Stick with such an Ubuntu, I would pay very much money to buy it, because I know that not only the USB-Stick is much more expensive than a CD but also the duplication of the Ubuntu-USB takes more time than a mass production of CDs.
Sad thing, that nobody sells it.

---

### Post by init1 on 2007-10-17
> **Cet said:**
> No, the question was not live persistence or plain live (btw, whats the difference?) but live persistence or install it, while you use it, like the CD.
If I would see such an USB-Stick with such an Ubuntu, I would pay very much money to buy it, because I know that not only the USB-Stick is much more expensive than a CD but also the duplication of the Ubuntu-USB takes more time than a mass production of CDs.
Sad thing, that nobody sells it.
I'm afraid I don't understand. I think you can install it just like you can while using the CD. Was that your question?
BTW, live means that it works like the CD does, no settings are changed. Live Persistence means that the changes are saved back to the USB drive, so any changes you make, like adding Firefox bookmarks, or changing the theme, will be there when you use it again.

---

### Post by Cet on 2007-10-19
> **init1 said:**
> I'm afraid I don't understand. I think you can install it just like you can while using the CD. Was that your question?
BTW, live means that it works like the CD does, no settings are changed. Live Persistence means that the changes are saved back to the USB drive, so any changes you make, like adding Firefox bookmarks, or changing the theme, will be there when you use it again.

Did you tried it?

Three things I want the USB-Stick to do:
1. Install Ubuntu on the Computer, if I want.
2. Not installing Ubuntu on the Computer but using it in live modus.
3. Saving the changings to the USB-Stick, if I use it in live modus.

Number 3 is impossible with the live CD, as it is only ROM.
Number 1 is impossible with the persistent USB-Stick, but I hope someone someday will approach all three aims on an USB-Stick.

---

### Post by init1 on 2007-10-19
> **Cet said:**
> Did you tried it?

Three things I want the USB-Stick to do:
1. Install Ubuntu on the Computer, if I want.
2. Not installing Ubuntu on the Computer but using it in live modus.
3. Saving the changings to the USB-Stick, if I use it in live modus.

Number 3 is impossible with the live CD, as it is only ROM.
Number 1 is impossible with the persistent USB-Stick, but I hope someone someday will approach all three aims on an USB-Stick.
Did you try to number 1 in live persistence? I'll try that sometime, and see if it works.

---

### Post by Burbruee on 2007-11-19
I agree, pendrivelinux is great. :)
I came across it last night while googling "linux over USB" or something like that, anyway so far everything is working great since I set it up for persistant so changes are saved. ( To include all my favorite applications )

But I have one big problem which I cannot solve.. Once the distribution has finished loading and I log in, I hear the login sound. I then try to play some music through rhytmbox and ot plays fine. But for everything else, it doesn't work! VLC, youtube videos over firefox, lbreakout2, blobwars and other games etc.. No sound..

Well, I got MPlayer running with sound once, however no audio plugin was chosen from the list, then I tried the different ones, oss, alsa, esd etc.. None which worked.

---

### Post by init1 on 2007-11-19
> **Burbruee said:**
> I agree, pendrivelinux is great. :)
I came across it last night while googling "linux over USB" or something like that, anyway so far everything is working great since I set it up for persistant so changes are saved. ( To include all my favorite applications )

But I have one big problem which I cannot solve.. Once the distribution has finished loading and I log in, I hear the login sound. I then try to play some music through rhytmbox and ot plays fine. But for everything else, it doesn't work! VLC, youtube videos over firefox, lbreakout2, blobwars and other games etc.. No sound..

Well, I got MPlayer running with sound once, however no audio plugin was chosen from the list, then I tried the different ones, oss, alsa, esd etc.. None which worked.
Try running
```

alsaconf

```
And see if that works. 
Currently, I prefer making my own Debian Live build with Liver Helper. In fact, Pendrivelinux used it in their official distro. The instructions are here, and they're very easy to use. [http://www.pendrivelinux.com/2007/05/31/create-your-own-live-linux-cd-or-usb-distribution]("http://www.pendrivelinux.com/2007/05/31/create-your-own-live-linux-cd-or-usb-distribution")

---

### Post by Burbruee on 2007-11-20
> **init1 said:**
> Try running
```

alsaconf

```
And see if that works. 
Currently, I prefer making my own Debian Live build with Liver Helper. In fact, Pendrivelinux used it in their official distro. The instructions are here, and they're very easy to use. [http://www.pendrivelinux.com/2007/05/31/create-your-own-live-linux-cd-or-usb-distribution]("http://www.pendrivelinux.com/2007/05/31/create-your-own-live-linux-cd-or-usb-distribution")

Thanks, I knew about alsaconf, just haven't used it for a long time so I forgot the command for it.. :oops:
Sound is working everywhere now. 

Currently, I'm satisfied with pendrivelinux, but maybe in the future I'll try building my own live-disc. Thanks for the link, looks easy. :)

---

### Post by yehudah2002 on 2008-02-26
can you actually surf the web using Ubuntu on a USB as a Live CD without having to configure anything?

Please let me know as soon as you can...

---

### Post by wolfen69 on 2008-02-26
yes you can. it works the same as any install or live cd. plus it will remember any changes you make.

---

### Post by yehudah2002 on 2008-02-26
Well, it really isn't working for me.
I want to use the host computer's internet connection, and I don't want to configure anything, but it still doesn't work...
Please help me...

---

### Post by mmoralls on 2008-02-26
I have pendrivelinux on USB and trying it on my laptop and it boots up fine but I can't get on the 'net. It recognizes the ethernet interface and I can ping the IP of the laptop but not the gateway of my router. Does DHCP setup on the pendrivelinux conflict with DHCP on the laptop?

Any ideas? TIA

---

