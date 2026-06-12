---
title: "how to boot from CDR?"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by willfriedwald on 2008-04-25
am trying to install ubuntu on a vintage dell -

so far I can't even get the thing to boot from the CDR!

I keep starting and restarting with the live CD in the drive, but it keeps booting from windows just the same.

what do I do?  How do I tell it to boot from the CDR?


will (with almost no windows experience, as you can tell)

---

### Post by aeiah on 2008-04-25
you need to set the boot priority in the BIOS. in old computers the priority is usually:

floppy
hard drive
cd rom

you need to set the cdrom higher than the hard drive, so it looks there first.

you can usually get into the bios by pressing the delete key or somethnig during boot. it'll say something like 'press suchandsuch key to enter setup'

---

### Post by Zralou on 2008-04-25
Sounds like you need to go into the BIOS and set the drive booting order to make the CD first boot device.
If you are very inexperienced, I would not advise playing around in the BIOS tho', you can render your system un-usable if you don't know what you are doing.

Ssra Lou

---

### Post by Pevichaey5 on 2008-04-25
i'm assuming you downloaded the iso file correct?

if you put the cd in, do you see a .iso file?

you need to burn it as an image, poweriso is a very good program for this

---

### Post by Tatty on 2008-04-25
You need to tell your BIOS (the first part of your computer to load) to check your CD drive for an OS before it checks the Hard Drive.

To do this, reboot then at the very first screen you see you will need to press a certain key to get into the bios settings.  The key is different for different motherboards but is usually one of the F-keys or the Del key.  Sometimes it tells you which one it is on the screen  (eg. Press Del to enter setup).
It might take a few attempts to do this if it doesnt tell you which key it is.

In there you will find some sort of place to set the boot order / boot priority, make sure you have your CD drive before your Hard Drive.

---

### Post by willfriedwald on 2008-04-25
thanks for feedback!

(1) I remember I did this with the liveCD in the previous edition of Ubuntu - this was around last August - and then I had no problem; the Dell booted from the liveCD (somehow, I don't recall doing anything different - I just put it in the drive and it worked.)

(2) this is what's confusing: there doesn't seem to be any opportunity to do anything, it just automatically powers on and I see the windows start-up screen, I don't see anything relating to the BIOS or start-up options - just straight to windows... will try again...

have no idea at what point I would push the BIOS setting key - and on top of that I don't know what key to push!

thanks!

Willfriedwald

---

### Post by Tatty on 2008-04-25
The best thing to do in that situation is to try each function key and the del key.  id start with F2 then F12 then Del, as these are common ones for bios, after that try each other F key.

Start pressing it as soon as you power-on, and keep pressing it repeatedly.  If you see the windows logo then you have missed it.

---

