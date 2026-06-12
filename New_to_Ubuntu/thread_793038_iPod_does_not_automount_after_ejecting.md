---
title: "iPod does not automount after ejecting"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by abhiroopb on 2008-05-13
So I finally managed to get amarok configured properly to use the iPod.

1. used this guide here to set it up so that my 80gb black classic iPod can be used ([http://ohioloco.ubuntuforums.org/showthread.php?t=658523](http://ohioloco.ubuntuforums.org/showthread.php?t=658523)).

2. I can connect it on amarok, I transfer music and then I update the artwork.

3. When I click disconnect (my post disconnect command is umount %d && eject %d - found it on amarok website I think) it disconnects and I can see the iPod ejecting.

4. I can browse my music without any issue including seeing the artwork.

PROBLEM:

5. When I plug the iPod back into the computer, nothing happens, absoloutely nothing.

6. Checking fdisk -l, I can see where the iPod is, and I mount it manually, I then have to delete the iPod_Control folder (actually I only have to delete the iTunes folder, but the database gets screwed up so it makes sense to delete everything), unmount the iPod and then do a hard eject (as I can't see any other way to eject the iPod properly).

7. Connect it to amarok and it connects fine, asks if I want initialize the database (as I have obviously deleted it).


This problem ONLY seems to occur if I actually add songs to the iPod. If I were to connect the iPod and then disconnect it (without adding any songs), upon reconnection it would appear fine.

This is obviously VERY annoying, as it means I can add songs once, and then have to delete everything in order to add it again!!!

Help please!

---

### Post by 13thfloor on 2008-05-13
I didn't read this before posting on the other thread - I had to leave.  My response might actually help you out.

---

