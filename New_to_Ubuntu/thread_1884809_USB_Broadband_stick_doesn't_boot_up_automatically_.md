---
title: "USB Broadband stick doesn't boot up automatically anymore."
date: 2011-11-22
forum: New to Ubuntu
---

### Post by suomalainen on 2011-11-22
Ubunteros,

I have a Huawei USB broadband stick that use to work as follows. As long as stick was plugged into a USB port the data connection would automatically connect after boot-up.

Nowadays, after boot up no connection is made automatically. TO MAKE IT HAPPEN, I simply need to only remove the USB stick and plug it back in. Then a connection is made.

I guess something must have gotten screwed-up during an update. What can I do so that my stick connects automatically again after bootup?

Thank you.

---

### Post by ask_ on 2011-11-22
in your network settings, for your connection profile , is "connect automatically" on?

Perhaps, it is on , as it connects automatically after you re-plug. But I also have a Huawei USB stick, and it also gives me problems sometimes. It works in some USB ports on my PC but not on others.

---

### Post by suomalainen on 2011-11-22
The connect automatically box it ticked and I'm using same USB as always.....

---

### Post by audiomick on 2011-11-22
Hallo Soumalainen.
Firstly, as far as I know, my Huawei stick never worked if it was plugged in before booting. This is for Ubuntu 10.04.

What version are you on now? Did an update cause the behaviour to change, or can you pinpoint any other reason?

---

### Post by suomalainen on 2011-11-22
Hei audiomick!

I use 10.04LTS. After original install my stick connected immediately upon boot up. Never had to take it away then plug it back in before. Only exception to this rule is if you do a "restart".

I think this could have been caused by an update. Don't know.

---

### Post by audiomick on 2011-11-22
Hmmm, I'm not much help, I'm afraid.

It turns out that mine ***does*** want to connect if it is plugged when the machine boots. I was sure it didn't, but I was wrong...

Anyway, I couldn't make it ***not*** want to connect, even by turning on the wireless, which I also thought disabled it.

I also ran the update manager. The machine hadn't been updated for some weeks, maybe even a month or so. I have it set to not update automatically. I thought that maybe I would catch an update that would cause the same behaviour, but it didn't. Still works properly after the updates, so I reckon that is unlikely to be your problem.

The only thing that occurs to me is to have a look with
```
sudo lsusb
``` 
after you have booted with the thing plugged in and it hasn't wanted to connect automatically and see if it is appearing on the usb port or not. That should at least narrow it down to a problem with the usb recognition or a problem with the network manager.

---

