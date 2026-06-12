---
title: "&quot;Offline Installation&quot; for Ubuntu"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Jackfrost123 on 2008-07-01
Hey ya all! How's everyone? 

I 'd like to install hardy "offline". That is while already loged in and runing a ubuntu installation to install a new ubuntu filesystem on one of my usb hard drives so when I take and put it on another computer it will boot up from there. Any ideas? Is this possible?

---

### Post by kuja on 2008-07-01
It's possible to install it to a usb flash drive, but it's not super simple. Try this: [http://lifehacker.com/software/ubuntu/how-to-install-ubuntu-linux-on-a-flash-drive-245087.php](http://lifehacker.com/software/ubuntu/how-to-install-ubuntu-linux-on-a-flash-drive-245087.php)

---

### Post by cariboo on 2008-07-01
The easiest way to do this is to disconnect your internal hard drive and then install on your external.

Jim

---

### Post by Jackfrost123 on 2008-07-01
Hey Kuja, thanks a lot for your help. There's already an app out there, can't recall its name but I can find it if neccesary that makes almost every linux live cd installation out there into a "live usb". It is of course a super useful app. which helped me out a lot when trying to intall ubuntu to my lappie where the cd drive doesn't work. I am not sure if the lifehacker advice is any good because I think I tried it before unsuccesfully. But in any case that's not what I am looking for right now. I am looking to install ubuntu on a usb hard drive, or for that matter on any hard drive other than the primary drive and while already in another ubunt file system.

Hey Jim, swap drives you mean? Yeah, well, that is the simplest one but I don't want (if I don't have to) go to the hassle of disconnecting and reconecting drives if I can do it from within ubuntu.

---

### Post by kuja on 2008-07-01
You can intall it to the external drive and then install grub to it afterwards if (and it probably will, unfortunately) the ubuntu installer puts grub on the wrong drive (ie: the internal). 

It'll probably involve, after booting, running ```
sudo grub
``` then, in the grub shell, ```
root (hd1,0)
```(0r similar, depending on what it calls your external, probably something like that though), then ```
setup (hd1)
```

---

### Post by Jackfrost123 on 2008-07-01
Ah, ok, I see, thanks a lot. So you are saying, because it's a bit different from what I am asking, that I exit ubuntu, boot with the cd and have it installed on the usb hd and then change grub file to make up for the error created by the setup, right?

---

### Post by kuja on 2008-07-01
Ah, yes, and while we're on the topic. You'll have to fix the grub for the internal drive too, so you'd one way or another boot into the internal drive's install, unmount/disconnect the external drive if neccessary, and perform the above steps, except using the devices hd0 instead (assuming grub it picks up the internal drive as hd0 .... I hope grub 2.0 fixes much of the mess that grub has trouble with ....)

---

### Post by Jackfrost123 on 2008-07-01
Hey, that's some great help, I can see why a grub 2.0 would be required.

---

