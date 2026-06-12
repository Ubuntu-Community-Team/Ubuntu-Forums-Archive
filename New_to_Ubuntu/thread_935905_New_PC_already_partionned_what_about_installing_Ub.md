---
title: "New PC already partionned what about installing Ubuntu"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by D4J0K3R on 2008-10-02
Hi, I finally bought a new PC & of course it's pre-installed with Vista =(
My hard-drive is already partionned in 2 & I want to install Ubuntu as my main OS but can I still install it if my HDD is already partionned?
I'll probably download wubi to make it easier for me since I'm not a computer wiz.

Thank in advance for your help!

D4J0K3R

---

### Post by SuperSonic4 on 2008-10-02
Yes you can, in fact it makes it easier not harder since you don't have to partition it yourself. Obviously it depends on the size of your partition whether you can install ubuntu but 10-15gb is considered a good minimum. You can use the live cd to install to the existing partition

---

### Post by D4J0K3R on 2008-10-02
Thank you for your clarifications but, I forgot to say one thing, I want to make another partition.
Now I have C: & D:, but I want C:, D: & E: as partitions for my HDD.
Will wubi allow me to create a new partition?

THank you SuperSonic4

---

### Post by hyper_ch on 2008-10-02
no, wubi will not allow you. You will need to shrink one partition and then make a new one for ubuntu to install - if you just want to have three partitions...

---

### Post by Panzor on 2008-10-02
I'd recommend using Gparted for the task above. Download the .iso from their website and burn the image to a disk, boot in that, and resize/move/create/whatever your new partitions to what you want. It may seem like a pain to make ANOTHER CD, but I've had mine for a year now and use it often enough to keep it pretty close to the front in my CD case. Good luck :).

---

### Post by oldos2er on 2008-10-02
You haven't said whether or not you want to keep Vista. It would be easier to advise you if we knew.

---

### Post by LowSky on 2008-10-02
HOLD on, why do you have 2 partitions, is one a recovery partition (did you computer come with a Windows or software CDs?
If you have no CDs be wary of installing Ubuntu, because if you do the install wrong you might not be able to return to Windows.

---

### Post by jerome1232 on 2008-10-02
It's not really any different than if you had one partition to begin with. 

You would want to shrink the partition that vista is on, and install Ubuntu to the freed up area.

If you use wubi it will create a file on the existing windows drive and treat that file as if it were a hard drive, no need to repartition. Although you will lose some performance on disk access operations while in Ubuntu.

(I have a wubi install on my laptop and I haven't noticed a difference, it's miles faster than vista even as a wubi install)

---

### Post by D4J0K3R on 2008-10-02
Wow so many answers thank you everyone!
Thank you Panzor for Gparted.
oldos2er: yes I want to keep Vista...
Speeking of wich, I heard that with newer computers you can run into trouble if you want to install Win XP on it.
Is it true?
I highly doubt it.
LowSky: I bought my PC and the 2 partitions we're already there.
500gb split 1/3 2/3, 1/3 for vista.
No software CD unfortunately.
& THank you jerome1232 for those clarifications.

Such a great forum!

---

