---
title: "how can i image 2 drives in raid0?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by bradlewa on 2008-04-30
i just finished installing ubuntu 8.04 on 2 drives in raid0.  they are both 320 gb drives.  i want to make an image of my system now (while it's fresh) so i can revert to it if i end up making a mistake.  i'm used to drive imaging in windows (i've used acronis true image there).  i've tried a couple of programs so far to image my raid0 configuration, but with no success.

i've tried the acronis true image boot cd, but it doesn't recognize the raid0 configuration as a supported partition type and then tries to make a massive image of the entire 2 disks, which is clearly not ideal.  i think there's something like 2 gb of data on the drives right now.

i've also tried partimage on the system-tools live cd, but it can only make images of individual partitions, and even then it still doesn't recognize the raid0 configuration properly.

lastly i tried the clonezilla live cd, but again, it didn't recognize raid0 as supported and tried to image the whole drive.

does anyone know if there's a program that can recognize raid0 in order to make an image?  maybe i'm just wasting my time since it's only 2 gb of data, and the install wasn't that painful - i suppose i could always just re-install if i end up screwing up my system.  but if anyone knows of something else, please let me know.

thanks.
bill

---

### Post by xcafeus on 2008-11-15
similar problem here... have you found a solution yet?

---

### Post by Kellemora on 2008-11-15
Your best solution is to DUMP the RAID and simply mirror one drive to the other and keep them as independent drives.  

You don't gain or lose any space, but have the security you can't get in a Raid configuration.

I hate to sound like a stuff shirt!

But, Raid only works from the controller that built the Raid, if it fails, you're sunk completely!  The odds of finding an exact duplicate controller 2 or 3 years from now is next to impossible.  You could of course buy an extra controller now while they are still available.
But that's a lot of expense and may still not work.  Depends upon what goes wrong with your Raid system.

Even Raid 5 is like playing with matches and a can of gas unless you have a full backup of the system.
Besides, Raid will be obsolete within a year, it's already hit it's limitations.

TTUL
Gary

---

