---
title: "Interface messed up"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by PizzaWednesday7 on 2008-06-30
So I'm pretty new to Ubuntu but i was sorta getting the hang of it until this morning and all the sudden my computer won't boot up right. The other day it wanted to do a automatic file system check and it said it couldn't and there was some scary black screen with a bunch of numbers on the left hand side that just kinda counted up and stuff but i fixed that somehow. Anyway when i go to boot up today it'll get to the log in thing but it'll say it cant load the right interface and it looks really old instead. So i type in my password and stuff then it tells me it can't load the network manager and a few other things. My desktop just looks like a bunch of little papers and all the folders are just little papers too and i can't really do anything. Theres no menu of applications and stuff at the top and I've got no idea what to do. Sorry if I'm being dumb but i tried to use the recovery mode thing and that didn't help and i don't know much about it to start with.

---

### Post by billgoldberg on 2008-06-30
> **PizzaWednesday7 said:**
> So I'm pretty new to Ubuntu but i was sorta getting the hang of it until this morning and all the sudden my computer won't boot up right. The other day it wanted to do a automatic file system check and it said it couldn't and there was some scary black screen with a bunch of numbers on the left hand side that just kinda counted up and stuff but i fixed that somehow. Anyway when i go to boot up today it'll get to the log in thing but it'll say it cant load the right interface and it looks really old instead. So i type in my password and stuff then it tells me it can't load the network manager and a few other things. My desktop just looks like a bunch of little papers and all the folders are just little papers too and i can't really do anything. Theres no menu of applications and stuff at the top and I've got no idea what to do. Sorry if I'm being dumb but i tried to use the recovery mode thing and that didn't help and i don't know much about it to start with.

Reinstall the ubuntu desktop.

You'll need to access a terminal, can you still navigate to it using "applications -> accessories -> terminal"?

If not, press ctrl+alt+f1 (enter login name and password ) and type in 

```
sudo apt-get install ubuntu-desktop
```

That should fix your problems, but I've never done this before.

There could be less drastic solutions, but this should work.

---

### Post by PizzaWednesday7 on 2008-06-30
Hmm well i tried that but it didn't really help. It still says it can't display "x-nautilus-desktop:///" and the human theme and stuff. Thanks anyway though

---

### Post by billgoldberg on 2008-06-30
My bad, try

sudo apt-get reinstall ubuntu-desktop.

It might be better to first remove the desktop and then reinstall it, so if the first command shouldn't work , try this:

sudo apt-get remove --purge ubuntu-desktop

should do the trick

then do 

sudo apt-get install ubuntu-desktop

---

### Post by PizzaWednesday7 on 2008-06-30
Well the terminal just tells me "E:invalid operation reinstall" i made sure i typed it right though. I dunno

---

### Post by billgoldberg on 2008-06-30
> **PizzaWednesday7 said:**
> Well the terminal just tells me "E:invalid operation reinstall" i made sure i typed it right though. I dunno

When booting up, choose to boot up in the command line in grub (don't know how it's called, it's in there. I believe it's the repair option, but I'm not sure).

Then either do the "reinstall" or "the remove and install" from my previous post.

write them down first (needs to bee 100% the same).

I believe it said "invalid operation", because the ubuntu-desktop was still running.

Note: you can always install install the ubuntu-desktop package from the cdrom, should your internet connect drop out or something, just in case. Just use the same commands when the cd is in the drive (do not boot into the live cd).

---

### Post by PizzaWednesday7 on 2008-06-30
Ok the reinstall thing didn't work again i don't know why but i think i'm going to just reinstall from the disk either way. should i just let it partition the disk again? Thanks for the help too, sorry

---

### Post by billgoldberg on 2008-06-30
> **PizzaWednesday7 said:**
> Ok the reinstall thing didn't work again i don't know why but i think i'm going to just reinstall from the disk either way. should i just let it partition the disk again? Thanks for the help too, sorry

I don't know why it didn't work.

But yeah a simple reinstall should be faster than wasting hours/days on trying to fix the problem.

First make sure you backed up all the data you want to save.

Then in the ubuntu installer, let it use the entire drive.

---

### Post by PizzaWednesday7 on 2008-06-30
Alright i think i'll be all set again soon. Thanks a lot for your help

---

### Post by PizzaWednesday7 on 2008-06-30
Well never mind i lied. Now it doesn't want to partition the disk. I'd rather make a new partition than use the whole disk because I've got Windows on the partition (though that doesn't run either) and if i kept it i could get the little bit of data i have from my other ubuntu right? I've got five devices listed /dev/sda which is like the whole system right? and then /dev/sda1,2,5 and 6. sda5 is the big one with 171565MB should i try to put a new partition in that one? Sorry I'm so clueless

---

