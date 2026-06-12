---
title: "moving parts in computer when sleeping?"
date: 2012-01-15
forum: New to Ubuntu
---

### Post by blackbird34 on 2012-01-15
Hi

When you put your laptop to sleep, do any moving parts (hard drive...) keep moving, or do they stop completely? does suspend-to-ram mean that the hard drive and all moving parts are turned off?

---

### Post by Cheesemill on 2012-01-15
When you use sleep/suspend/standby then the computer only uses enough power to keep the data in RAM intact, so the drive shouldn't spin.

If you hibernate then it will turn of completely and not use any power.

---

### Post by Double.J on 2012-01-15
^^^ +1 ^^^

Additionally your fan(s) may still run - the temperature has to be kept under control after all :) If you're trying to trace a sound.. could be the place to start!

As Cheesemill says Hibernate will power down completely - the contents of your RAM is copied to swap, then loaded back into RAM when you power on :)

The setting "save to RAM" that you mentioned is often a hibernate feature - this doesn't copy to swap, your session is saved in RAM and power is used to keep the RAM going, just like sleep as you mentioned, so the fan may apply again. To save to swap and power down completely, it's usually called "save to disk" 

Hope it helps!

---

### Post by blackbird34 on 2012-01-16
Thanks for the quick replies!
It's just me wondering if it's safe to cart my computer around asleep, from the point of view of avoiding doing so if something moving, like a hard drive, might get damaged. It is a lot more practical to merely wake it up when i arrive in class, rather than waiting 30-45 seconds to turn it on.

(Edit: it won't hibernate any more for some reason. Something to do with the swap memory and multibooting, i think. Haven't had time to find out why. Any ideas, O gurus? =D )

---

### Post by sandyd on 2012-01-16
> **blackbird34 said:**
> Thanks for the quick replies!
It's just me wondering if it's safe to cart my computer around asleep, from the point of view of avoiding doing so if something moving, like a hard drive, might get damaged. It is a lot more practical to merely wake it up when i arrive in class, rather than waiting 30-45 seconds to turn it on.

(Edit: it won't hibernate any more for some reason. Something to do with the swap memory and multibooting, i think. Haven't had time to find out why. Any ideas, O gurus? =D )
Main things to check if its not hibernating.
a) Swap should be larger than ram. Actually, thats a bit incorrect. There should be **more** free space in the swap then the RAM at time of hibernation.

b) If you encrypted your home directory, hibernation won't work cause your swap is encrypted. [This is currently being worked out in brainstorm.]("http://brainstorm.ubuntu.com/idea/29055/")

---

### Post by Cheesemill on 2012-01-16
> **sandyd said:**
> 
a) Swap should be larger than ram. Actually, thats a bit incorrect. There should be **more** free space in the swap then the RAM at time of hibernation.[]("http://brainstorm.ubuntu.com/idea/29055/")

Not strictly true. You can often get away with less swap than RAM because the image stored in the swap file is compresed.

---

### Post by blackbird34 on 2012-01-16
Thanks
I have 2 GB of RAM and 2.93 GB of swap and my /home isn't encrypted, so it isn't either of those. I tried formatting the swap partition and moving it somewhere else once, all that did was make me have to reinstall GRUB:popcorn:
So in fact the swap partition is not the same one as when I first installed. Would this affect the /etc/fstab file or config files  like that, that configure how all the disks load? Like fstab trying to get the computer to hibernate in a partition that doesn't exist? 
When i type Hibernate in Synapse, it locks the screen.... When I type "suspend" "shutdown" or "restart", Ubuntu does what i say - fast:D. So i think it must be some problem somewhere in the config, but don't really know where to do the digging...

EDIT: is it possible to change the title? adding "hibernate issue" to it would be more relevant :D

---

### Post by sandyd on 2012-01-16
> **Cheesemill said:**
> Not strictly true. You can often get away with less swap than RAM because the image stored in the swap file is compresed.
*shrug*
Its just to make sure that it would hibernate.

Im not a person to check to see how much my image would compress when my computer hibernates. I have better things to do than that...

---

### Post by sandyd on 2012-01-16
> **blackbird34 said:**
> Thanks
I have 2 GB of RAM and 2.93 GB of swap and my /home isn't encrypted, so it isn't either of those. I tried formatting the swap partition and moving it somewhere else once, all that did was make me have to reinstall GRUB:popcorn:
So in fact the swap partition is not the same one as when I first installed. Would this affect the /etc/fstab file or config files  like that, that configure how all the disks load? Like fstab trying to get the computer to hibernate in a partition that doesn't exist? 
When i type Hibernate in Synapse, it locks the screen.... When I type "suspend" "shutdown" or "restart", Ubuntu does what i say - fast:D. So i think it must be some problem somewhere in the config, but don't really know where to do the digging...

EDIT: is it possible to change the title? adding "hibernate issue" to it would be more relevant :D

Post output of```

free -m
```

---

### Post by Cheesemill on 2012-01-16
Sorry. Just being pedantic. :)

---

### Post by sandyd on 2012-01-16
> **Cheesemill said:**
> Sorry. Just being pedantic. :)
:P .
Like I used to be before I started this tour.

---

### Post by blackbird34 on 2012-01-16
```
nad@nad-Presario-CQ56-Notebook-PC:~$ free -m
                                total       used       free     shared    buffers     cached
Mem:                            1944       1618        326          0        143        711
-/+ buffers/cache:                         763       1180
Swap:                             0          0          0


```I moved everything over with spaces for clarity but that's the numbers that came out...

Also added a screenshot of GParted showing the UUID of the Swap partition i have now, and a copy of my fstab. 
What i was talking about in my post #7 further up might be the problem... Is it safe to just change the swap UUID in fstab so it fits the UUID of the actual swap partition?

---

### Post by sandyd on 2012-01-16
> **blackbird34 said:**
> ```
nad@nad-Presario-CQ56-Notebook-PC:~$ free -m
                                total       used       free     shared    buffers     cached
Mem:                            1944       1618        326          0        143        711
-/+ buffers/cache:                         763       1180
Swap:                             0          0          0


```I moved everything over with spaces for clarity but that's the numbers that came out...

Also added a screenshot of GParted showing the UUID of the Swap partition i have now, and a copy of my fstab. 
What i was talking about in my post #7 further up might be the problem... Is it safe to just change the swap UUID in fstab so it fits the UUID of the actual swap partition?
ah ha!
your swap isn't mounted.

Run 
```

sudo nano /etc/fstab

```Change
```

UUID=1d4e0322-3342-4cf1-a2f2-13d6fecf8c7b
```to the new swap uuid
```

UUID=1a6e0cf2-2c44....
``` youll have to copy the rest of the UUID yourself (replace the dots), I can't find my glasses.

---

### Post by blackbird34 on 2012-01-17
I did that. I checked in GParted the swap partition was mounted, then tried to Hibernate (pull up Synapse and type until it suggests Hibernate - this works for Suspend, Restart and Shutdown perfectly).

Still won't hibernate... The only thing I haven't tried that i can think of is: is there a Terminal command for hibernating? WHen I couldn't get the GUI to do a shutdown or log out (Before Synapse) I used to do that.

---

