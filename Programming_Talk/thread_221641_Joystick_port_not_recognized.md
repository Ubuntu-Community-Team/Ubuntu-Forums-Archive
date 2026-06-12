---
title: "Joystick port not recognized"
date: 2006-07-23
forum: Programming Talk
---

### Post by cwc on 2006-07-23
I'm trying to write a program that reads/writes data to the joystick/game port in my Ubuntu machine. There are no /dev/js* devices nor anything in /dev/input for the game port. I have tried loading the joydev and gameport modules, but neither creates the device entries. Can someone give me a hint on how to recognize my hardware?

---

### Post by fluffington on 2006-07-24
My USB gamepad (which Ubuntu recognizes automatically with no extra work or packages) is /dev/input/js0.

---

### Post by lopzided on 2006-07-24
> **fluffington said:**
> My USB gamepad (which Ubuntu recognizes automatically with no extra work or packages) is /dev/input/js0.

he's talking about a 'gameport' gamepad....not a USB gamepad...

i'm having the same problem....see my post here, [http://www.ubuntuforums.org/showthread.php?t=214191&highlight=gameport](http://www.ubuntuforums.org/showthread.php?t=214191&highlight=gameport) , which has been unaswered for awhile now....i don't think anyone knows ](*,)

---

### Post by fluffington on 2006-07-24
> **lopzided said:**
> he's talking about a 'gameport' gamepad....not a USB gamepad...

So he is. Oops. I've never attempted to use my game port with Linux, so I have no idea.

---

### Post by AR_Kozz on 2007-01-23
this might not get it to work, but to create just the device file in terminal it's something like go to /dev/input,

and 
sudo MAKEDEV js

it'll pop up

---

