---
title: "how can i install a second hard drive"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by hyperhopper on 2008-09-20
ok, in my hand i have a 30gb hard drive. i need it because after tf2 is done downloading i will have 1 gb left of hard drive space. how can I put the hard drive into the computer and in a way, combine it with the original. Chances are i wont move it untill i get a waaaay bigger one, and i just want it to contribute to the amount of resources my computer has available. how, once i put it in my comp, what do i do?

---

### Post by SuperSonic4 on 2008-09-20
If you're using a SATA drive (which are standard now) you get a SATA lead from one of the ports on the motherboard (mine are red) to the device. Afterwards connect a SATA power connectors from the PSU and screw into a 3.5" slot that's free. The original will recognise it in /media

As for combining the two into one big one that's impossible although you can leave the MBR on disc 1 and move the data to disc to.

Personally I'd leave configuration files and put fresh updates/installs onto disc 1 (30gb) and move the other files (such as video, music, pics and docs) to disc 2 which is partitioned however you like (my media disk has Partitions of Music, Documents, Pictures and Video) Disc 2's partitions will be in /media and available for disc 1 to see

---

### Post by halitech on 2008-09-20
check post #4 on this thread

[http://ubuntuforums.org/showthread.php?t=174562&highlight=mount+ext3](http://ubuntuforums.org/showthread.php?t=174562&highlight=mount+ext3)

---

