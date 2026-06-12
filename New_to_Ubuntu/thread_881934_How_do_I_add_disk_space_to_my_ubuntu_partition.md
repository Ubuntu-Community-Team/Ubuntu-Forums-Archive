---
title: "How do I add disk space to my ubuntu partition?"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by bmann11 on 2008-08-06
I'm getting alerts in a couple of apps, evolution and oo, that I can't save because I'm out of room.  Is there an easy way to increase the partition from the windows side of things?

Also, how would I go about kicking windows to the curb?  I haven't used it in months but it's still taking up space.

---

### Post by eriqjaffe on 2008-08-06
You can use gparted to resize partitions, either through the Ubuntu CD or through gparted's own Live CD.

To remove Windows completely, just delete the partition it's on and resize your Ubuntu partition(s) to fill up the empty space.

---

### Post by bmann11 on 2008-08-06
is there a way to repartition without using the cd.  I'm in Brazil and my cd is in Montana

---

### Post by mick8985 on 2008-08-06
Not if your ubuntu install is all in one partition, as you will need to unmount your root partition to do this.

---

### Post by ajgreeny on 2008-08-06
You obviously have an internet connection so download gparted live CD from [here]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779") and burn it and you can use that.  It's not a big download and it is worth having around as it boots quicker than ubuntu liveCD, in my experience.

---

### Post by bmann11 on 2008-08-15
I downloaded the gparted live iso, opened up Brasero to burn the image onto the cd, and then I got an error message saying "the selected disc does not have enough free space to store the disc image."

However, Brasero tells me that the disc has 702 MB of free space prior to trying to burn it, but the size of the iso is 90 MB.Any ideas?

---

### Post by Too Late on 2008-08-15
Brasero says that in the hard disk there's no space to (temporarily) store that disc image, which is to be burn. If you can't clean up any space on your linux partition, you should maybe burn that disc in Windows.

---

### Post by bmann11 on 2008-08-15
Thanks to another post just below mine, I burned the image using the ole' right click method.  So, I now have the image on a disc, how do I proceed?


By the way, Brasero looks like it could be a great app if only the last, and most imortant step, worked.

---

