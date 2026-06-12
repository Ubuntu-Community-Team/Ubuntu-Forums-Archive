---
title: "[SOLVED] Wireless/Terminal trouble"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by themissinglink1 on 2008-08-19
I have been trying to use my device drivers from my windows partition to set up a wireless internet connection. I have been advised to use this by a friend:

[B]sudo mount -t ntfs/dev/hda1/mnt
sudo cp/mnt/windows/system32/drivers/_mydrivers.sys_/etc/ndiswrapper
sudo cp 'find/mnt -iname _mydrivers.inf'_/etc/ndiswrapper
sudo unmount/mnt

sudo dpkg -i/media/cdrom0/pool/main/n/ndiswrapper*
sudo ndiswrapper -i/etc/ndiswrapper_mydrivers.inf_
sudo ndiswrapper -m
sudo modprobe ndiswrapper [/B]

However at **sudo cp/mnt/windows/system32/drivers/mydriver.sys/etc/ndiswrapper** a command not found warning appears. Is this because i am using the wrong driver location? Have i mounted the wrong drive... i have tried both drives and all driver locations under system-hardware-device drivers-properties however i seem to get the same message every time. If i am making sense :) any advice you could give would be greatly appretiated. Thanks in advance.

Chris

---

### Post by nothingspecial on 2008-08-19
You need a space after cp

---

### Post by themissinglink1 on 2008-08-19
really as simple as that??? i am such an idiot. I don't really know what i am doing so just followed the instructions exactly. I'll try it out and get back to you. :lolflag:

---

### Post by cdtech on 2008-08-19
```
sudo mount -t ntfs /dev/hda1/mnt
sudo cp /mnt/windows/system32/drivers/mydrivers.sys /etc/ndiswrapper
sudo cp 'find/mnt -iname mydrivers.inf' /etc/ndiswrapper
sudo unmount /mnt

sudo dpkg -i /media/cdrom0/pool/main/n/ndiswrapper*
sudo ndiswrapper -i /etc/ndiswrappermydrivers.inf
sudo ndiswrapper -m
sudo modprobe ndiswrapper 
```

I just copied and pasted the commands you had and spaced them properly. You should be able to see the difference between yours and this one.

> i am such an idiot.
Thats not true. Your just learning as we all have. Don't ever be afraid to ask.

---

### Post by nothingspecial on 2008-08-19
I don`t know about the whole thing but it would seem to me that it would be easier to download the drivers and install them using ndisgtk.

---

### Post by nothingspecial on 2008-08-19
> **cdtech said:**
> ```
sudo mount -t ntfs /dev/hda1/mnt
sudo cp /mnt/windows/system32/drivers/mydrivers.sys /etc/ndiswrapper
sudo cp 'find/mnt -iname mydrivers.inf' /etc/ndiswrapper
sudo unmount /mnt

sudo dpkg -i /media/cdrom0/pool/main/n/ndiswrapper*
sudo ndiswrapper -i /etc/ndiswrappermydrivers.inf
sudo ndiswrapper -m
sudo modprobe ndiswrapper 
```

I just copied and pasted the commands you had and spaced them properly. You should be able to see the difference between yours and this one.

Sorrry didn`t look that way to me :oops:

Edit Just read your post properly - I thought you were saying there was a space. Double oops.

---

### Post by tim2706 on 2008-08-19
[SIZE="7"]hello go to : Help-with-linux.webeden.co.uk for linux live help in the next hour only (until 2 pm) see you soon[/SIZE]

---

### Post by themissinglink1 on 2008-08-19
sorry i just tried this and i now get a **"missing file destination operand"** message. Is this a wrong location in the windows side?

*"I don`t know about the whole thing but it would seem to me that it would be easier to download the drivers and install them using ndisgtk."*

I checked and there doesn't seem to be any linux versions of my drivers. If this however is not what you mean i would be happy to try what you are saying?

---

### Post by nothingspecial on 2008-08-19
I have to sleep now but -
```
sudo apt-get install ndisgtk
```
It allows you to install windows drivers.

---

### Post by nothingspecial on 2008-08-19
See here
[http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)

---

### Post by themissinglink1 on 2008-08-19
Managed to get it fixed thanks guys! :):)

---

