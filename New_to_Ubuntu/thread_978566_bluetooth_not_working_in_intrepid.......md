---
title: "bluetooth not working in intrepid......"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by techno-mole on 2008-11-11
hello all

this is another bluetooth related post, and after some searching i have yet to find an answer to my problem.

the problem is that i have (like a lot of people) have a usb bluetooth dongle, which i use to connect my mobile to the pc with, now since hardy this has not worked correctly, in fact bluetooth for me has not worked since gutsy.

the problem is this, in gutsy i would plug in my bluetooth dongle and the system would detect it and load the app to run it, i could then set about pairing my phone with the pc etc.
  but in hardy this stopped working, well it would still show an icon and i could still configure various things, however when i tried to pair the phone with the pc it would lock the system up and the lights on the keyboard would flash (caps lock etc) and the only way i could get the system back to a usable state was to press the reset button on the tower.
 i did post a bug report about this, but nothing came of it.

so when i upgraded to intrepid i was hopeful it would work, but alas it doesnt, i can plug the dongle in and nothing happens, by that i mean nothing, no icon appears in the system tray, nothing happens at all, if i do " lsusb " in a terminal it shows that the device is plugged in, and i assume it also means the system knows its there, but it just doesnt load anything to use it.

  i have tried pairing from the phone to see if the phone sees the pc but it doesnt, i have tried various things but with no luck, it is quite useless, i have 2 different dongles and neither work.

so has anyone else got this problem ? im not trying to use a bluetooth mouse or keyboard im just trying to use my dongle so as i can move files from phone to pc etc.

(on a side note, although the bluetooth didnt work correctly in hardy it did at least work on some level, which is more than can be said for intrepid, but i also upgrade hardy to use kde 4.1 and after i had done this the bluetooth stopped working altogether, by that i mean it did exactly as it does now, that being nothing, the icon stopped appearing etc etc)

cheers

---

### Post by khelben1979 on 2008-11-11
You could try to download the bluetooth stack and compile the source yourself. :)

[The BlueZ homepage]("http://www.bluez.org/").

It might work.

---

### Post by techno-mole on 2008-11-11
well i took your advice and tried compiling the packages myself, but i still get the same result.

ive seen a few articles about bluetooth and the kde base packages ? or something like that, it kind of indicated that some (or all) of the bluetooth packages are not yet compatible with kde 4, this would kind of confirm what i had originally thought about kde 4 and bluetooth not working together,
  i did mention it in my original post about how bluetooth (although it wasnt working correctly) seemed to stop altogether when i changed form kde 3 to kde 4 on kubuntu hardy, and seeing as intrepid uses kde 4 it would kind of hint at it being the cause of the problem.

this has made me wonder whether to go back to using ubuntu and gnome rather than kubuntu and kde 4 (i do like kde 4 though)

i may have a go once ive shifted the 42 gb of film files of my main system.

---

### Post by khelben1979 on 2008-11-11
Have you reported this issue to the KDE team?

---

### Post by Denestria on 2008-11-11
[https://wiki.ubuntu.com/IntrepidReleaseNotes#Kubuntu%20Bluetooth%20support](https://wiki.ubuntu.com/IntrepidReleaseNotes#Kubuntu%20Bluetooth%20support)
[https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/280997](https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/280997)

---

### Post by techno-mole on 2008-11-12
```
Kubuntu Bluetooth support

Bluetooth is not supported in Kubuntu 8.10 because KDE does not yet support the bluez 4.x stack required for compatibility with the kernel used in 8.10. A fix for this is being evaluated as a post-release update. (Bug 280997) 
```

this is what i meant by bluetooth not being supported in kubuntu 8.10, does seem odd to me that they wouldnt make sure something like bluetooth was working before they released it.

i read through the bug posted on launchpad (thanks for the link) i have reported it as a bug as well (while i was testing the beta of intrepid)

i found this posting 
```
I just aptitude installed bluez-gnome and ran bluetooth-applet
```

and although i had installed the gnome bluetooth packages using adept it hadnt worked for me, but after i tried compiling the packages myself with no luck i had removed anything bluetooth related from the system, so i thought i might as well try it, and strangley it worked (no idea why it didnt work installing the same thing using adept)

so now i have bluetooth working, i can pair and move files from device to device so for now its all working.

cheers for the help.

---

### Post by jwillar on 2008-11-12
This works, great solution; it even continues to work after a system boot.  I wonder why this had to be 'dug' out of the bug report and not offered immediately as an interim solution until 'kdebluetooth4' was perfected?     jwillar

---

