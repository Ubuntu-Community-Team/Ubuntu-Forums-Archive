---
title: "Upgrading Gutsy."
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Piteco on 2008-05-11
Hi, I want to upgarde my gutsy to hardy using the live cd 'cause I don't have a really fast conection. There is some way to do it with a single hd and without loosing all my /home/ things and without making a backup?

---

### Post by tjwoosta on 2008-05-11
well..

what i did was shrink the gutsy partition with gparted then install hardy next to it  
(this requires that you have enough free space to shrink it)

when everythings installed you can copy files from one partition to the other very easily

then if all goes well and you like hardy you can delete the old gutsy partition and expand the new hardy one

---

### Post by aysiu on 2008-05-11
You can't upgrade with the live CD. You can only install. As tjwoosta indicates, there are workarounds.

---

### Post by UnknownFear on 2008-05-11
That sounds like an awesome method if you want to experiment with other distros.

---

### Post by Piteco on 2008-05-11
> **tjwoosta said:**
> well..

what i did was shrink the gutsy partition with gparted then install hardy next to it  
(this requires that you have enough free space to shrink it)

when everythings installed you can copy files from one partition to the other very easily

then if all goes well and you like hardy you can delete the old gutsy partition and expand the new hardy one

I'm realy new with Ubuntu, can you send me some tutorial  of how-to-do-it, please?:)

---

### Post by tjwoosta on 2008-05-11
first you will need to boot the live cd then go to System-Administration-Partition Editor 

now with the partition editor you right click gutsy partition and click resize/move  

(just make however much freespace you want **at the end of the partition**) (i would make at least 10 GB preferably more)
also** its important that you have enough free space available on your gutsy partition to resize it, because if you make it too small it could possibly cause loss of data**
"but i think gparted has some sort of a prevention method anyway"

after you have all the unallocated space you want at the end of the partition just click apply 
(this could take a wile as it has to copy and move all your files)

after that just close the partition editor and click the install icon on the desktop

when you get to the point where it asks you how you want to install, just choose **"Guided Install: use largest continuous free space"**

this will install to the unallocated space you made and your done

---

### Post by SlappyPappy on 2008-05-12
Clever! Any dangers inherent there in trying to do it that way?

Just trying to figure out what traps one might fall into along the way with such a process.

---

### Post by Magnes on 2008-05-12
> **SlappyPappy said:**
> Clever! Any dangers inherent there in trying to do it that way?

If I remember correctly you can use Ubuntu Alternate CD (or better - the DVD) to upgrade. Don't know how though. It would be safer. Changing partitions always comes at risk.

---

### Post by tjwoosta on 2008-05-12
> Clever! Any dangers inherent there in trying to do it that way?

no, not really that clever, just common sense

of course anything that involves moving partitions does come with some risk of data loss however i have used this method to change operating systems and move partitions countless times and i have never had any problems whatsoever
vs all the people that i see on the forums who try to upgrade and end up having to reinstall clean because something went wrong

---

### Post by chewearn on 2008-05-12
> **SlappyPappy said:**
> Clever! Any dangers inherent there in trying to do it that way?

Just trying to figure out what traps one might fall into along the way with such a process.

Yes, there is one trap.

Grub second stage is now in the most recent install (hardy in this case).  If hardy don't work for you, you can't just wipe the hardy partition.  This will wipe grub stage 2 and you ended up with an unbootable harddisk.

The solution is to modify grub to point back to the original gutsy partition first.

---

### Post by tjwoosta on 2008-05-12
you could reinstall grub with the live cd (its not that hard, ive done it)

---

### Post by SteveNorman on 2008-05-12
Could you use this technique to share home with other distros? Or would a home folder not transfer distro to distro?

---

### Post by tjwoosta on 2008-05-12
yes, you can

look here
[http://ubuntuforums.org/archive/index.php/t-572395.html]("http://ubuntuforums.org/archive/index.php/t-572395.html")

---

### Post by Piteco on 2008-05-12
Thanks everyone, now is just wait the hardy cds arrive here :-D

---

