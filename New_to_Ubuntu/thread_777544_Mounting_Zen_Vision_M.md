---
title: "Mounting Zen Vision M"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by PDG1 on 2008-05-01
I've got a Zen Vision M and I'm trying to get it to mount as a file system
I realize that it's an MTP device... I tried to install MTPFS but it's not going as smoothly as I would like.

any ways... that's not my big problem, it's more of a side problem.

The Zen vision also has what it calls "the removable Disk mode" where it acts as a removable disk instead of an MTP device.
I think it's Vfat or something

when I first upgraded to Hardy Heron, it automatically mounted as a file system...
something when haywire and the bloody Zen shut down on me...
now I can't get it to mount worth beans
err... at least it doesn't automatically mount...

any idea why it has forsaken me?

Rock on
~Ryan

---

### Post by Hospadar on 2008-05-01
A note on mtpfs:  MTP doesn't really allow all the functions you need to mount it as a filesystem, so although mtpfs attempts to emulate a filesystem, you really arn't getting the total package.  So probably some of your issues with mtpfs are just due to the basic limitations of mtp.

As for removable disk mode, do you have the zen set to removable disk? (It has to actually show that on the screen to work as a removable disk, even though the data will hang around).  For example, If I had it set to removable disk, then my zen crashed, then I turned it back on, it wouldn't be acting like a disk until you go back into that mode.  If that doesn't even work, try hard resetting it with the little pin-hole button on the bottom, then go back into the disk, clear out the disk space by setting it to no disk at all, then back to the size you want and see if that works.

If you are looking for some stuff to just put songs on your player, I use gnomad or amarok.  gnomad is pretty straight foreward and I'm pretty sure it will let you put any kind of file you want directly onto your player (even if the player can't play it)

Also a side note, you might want to look into using iriverter to transcode movies for your player, it shrinks them down to the screen res and transcodes them to the right format.

---

### Post by PDG1 on 2008-05-01
ya... I do have it on the removable disk thingy...
I'm not too fond of the clearing out the removable disk section and starting over from scratch because I've got a crap load of pictures and stuff from my Germany trip that I'd like to put onto my computer

pretty much the only thing that I would use MTPFS for is moving/ copying files from it to my compy
the only problem is that I can't seem to get MTPFS to work @ all...
i can't seem to install it correctly either

I don't really watch videos on it that much anymore

Main thing I use it for is recording my guitar playing and listening to music in the car.
so iriverter isn't that useful to me

---

### Post by PDG1 on 2008-05-03
well... now it really doesn't matter because I think I know what's going on...
It's actually because my Zen is Dead
or at least dead in the ports

I think I remember it falling from a desk whilst in the dock...

so now I'm going to try and take it apart and fix it because there's no warranty and I would like to keep my files instead of just getting a new one

wish me luck, eh

---

### Post by jaybstn on 2008-05-07
Im having issues mounting my Zen player with 8.04. This was never a problem under 7.04 or 7.10; however now when I try to mount it with Amarok, the whole system freezes and I have to do a hard reboot, and with gnomad2 it (the program) just "hangs" and I have to force quit it. Any ideas?

---

