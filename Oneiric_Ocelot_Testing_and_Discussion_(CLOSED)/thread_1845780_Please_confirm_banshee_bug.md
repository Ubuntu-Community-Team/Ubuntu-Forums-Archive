---
title: "Please confirm banshee bug"
date: 2011-09-17
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by CaptainMark on 2011-09-17
If someone could confirm this bug before i go reporting to launchpad, this could depend on which device is being used, in fact honestly this might not be a banshee bug at all but with the mounting system, anyway,

basically when i 'disconnect' my ipod classic from banshee it unmounts the ipod but seems to issue it with a reset prompt too, it unmounts then resets and is redetected and remounted, its risky because if i pull it out while mounted it could bork it up, this doesnt happen when i unmount the ipod from unity launcher, anyone find this too??

---

### Post by ronacc on 2011-09-17
probably not a banshee bug , try selecting eject rather than unmount , this has been happening for awhile with usb drives which is probably what the system sees your ipod as .

---

### Post by cariboo on 2011-09-17
I agree with ronacc, it isn't a problem with Banshee, you can prove/disprove the theory by opening a terminal and typing the following command:

```
sudo eject /dev/sdxX
```

where /dev/sdxX = you ipod. I see the same thing, where the device is remounted, when choosing the safely remove option for any usb storage device

---

### Post by ronacc on 2011-09-17
you can also rt click on it in nautilus and select eject from the drop down menu .
edit : there was a bug on it but I can't find it now , maybe they invalidid it . I remember some discussion about it not being a bug but a "feature"

---

### Post by mc4man on 2011-09-18
It would seem there must be a hardware factor involved that accounts for varying behavior

At least here usb media is never remounted after eject or safely remove. (unity disallows unmount on eject-able media
usb flash, ipod and ext. dvd drives all work fine & as expected, even disconnect on an ipod in banshee (don't know the model - black, 1GB

However on usb hdd's, while never 'remounted', there is a 50% chance of a kernel panic when using 'safely remove'

There was this bug some time ago on the auto remount
[https://bugs.launchpad.net/ubuntu/+bug/608508](https://bugs.launchpad.net/ubuntu/+bug/608508)

---

### Post by CaptainMark on 2011-09-18
i also have a usbhdd that remounts itself when using the safely remove option, unmount from the unity launcher again works okay

---

### Post by ronacc on 2011-09-18
I found the bug , wonder why it didn't show up last night , there has been no action on it since maverick , it's confirmed but never triaged .
[https://bugs.launchpad.net/ubuntu/+bug/608508](https://bugs.launchpad.net/ubuntu/+bug/608508)

---

