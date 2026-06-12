---
title: "generic mp3 firmware/ OS customization"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by yragrelluf on 2008-09-21
I bought a few cheap generic mp3 players from ebay, and they all dont work right, but thats ok, because I want to use them for a project. I was wondering if anybody knew anything about stripping the existing firmware/OS embedded on the mp3 player, and installing something else, like rock box, but rock box's website seems to be pretty model specific? Id like to have them just work to play mp3's and view .jpg images.
Then heres the fun part!, one of them is 8gb, and Id like to set it up so that it works as a music player and image viewer for everyday use, but also be able to boot a computer from it using a lightweight OS like puppy linux or xubuntu, with minimal applications installed.
Any suggestions? Anybody ever done anything like this before? Is it possible?

---

### Post by Mornedhel on 2008-09-21
Every firmware is "pretty specific". That's in the definition of "firmware". You have to write it to be tailored to a particular set of components.

I'm afraid if RockBox doesn't support it, and if no other alternative firmwares out there (if there are any) do either, you'll have to write your own.

---

### Post by yragrelluf on 2008-09-21
So what about making the mp3 player a bootable media? The firmware issue can be fixed later.

---

### Post by mrsteveman1 on 2008-09-21
I stripped apart the firmware of one of those bestbuy insignia flash players a year ago, it was fun. Can't really do much with it though, can't install anything else on the device, can't really alter the firmware much if at all.

As long as it puts itself into usb-storage class mode by default you can use it however you want.

Sometimes the block size on flash devices is odd though.

---

