---
title: "Amarok and the IPod! A mounting solution"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by Ecopirate on 2008-06-22
Hey there. So my girlfriend just got an ipod a bit ago, and I'd been trying to figure out how to sync it to Amarok. I use Kubuntu with KDE4, and getting Amarok to recognize the ipod was becoming a source of aggravation. However, after sifting through a number of solutions that didn't work for me, I found it myself.

The situation: Amarok recognizes a storage device at /dev/sdb2
However, when attempting to designate this device in Amarok as the Ipod, it says that not ipod device is mounted. Attempting to manually define the ipod mount failed as well.

The solution: Set the device as an Ipod storage device. Click on the settings for the device (Should be at the top, to the right of the drop-down menu with the options. The little gears). Another window will come up with pre-connect and post-connect commands, as well as a few other options. The only thing you need to do is type in ```
mount %d
``` in the pre-connect box.

Voila! It should connect. At least, in my case, it did connect. Hope it helps!

---

### Post by BLTicklemonster on 2008-07-24
Hopefully you will save a lot of people some trouble with this post! Thanks for sharing!

---

### Post by Flyingjester on 2008-07-24
Good work finding a workaround :D

---

