---
title: "Question about my partitions"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by linuxnovice on 2008-06-03
Hi,

I have a toshiba tecra laptop with 120gb hard-disk. I have about 18gb mounted on / and 1.2 gb as swap and the rest mounted on /home running Kubuntu 7.10. I have a bunch of videos and music in the /home partition. Its too difficult to move them to another computer. So I would like to keep. But I want to partition my /home for the new Ubuntu 8.04 as the old one has config settings for KDE and I want to customize gnome from scratch.

So, using the live cd I resized /home and created a new partition of about 28gb which corresponds to the size of the stuff I need to backup. My intention was to move all the music/videos/docs etc to this new partition and NOT format during the new install so that I can have access to them later. I formated the new partition as ext3 which is the same fs for my other partitions. 

After doing this, I rebooted into Kubuntu. Ideally, I would like to mount this new partition to /backup or something and transfer the stuff I need there. But I cannot see the new partition that I created. My question is how do I get the new partition to show and access it so backup my stuff there.

Thanks.

---

### Post by indytim on 2008-06-03
You will need to:
1.  create a new directory (folder) in /media.  Name it to what you want the new partition identified to (like LxMedia etc).
2.  Edit your fstab and make a new entry for your new partition.  If you're uncertain about how to effectively edit your fstab file, do a brief search on any of the Ubuntu forums as this topic has been covered many, many times.
3.  Re-boot and your new partition should be mounted.  From there it is only a matter of using a file manager of your choosing to transfer the files over to the new parition.

IndyTim

---

### Post by louieb on 2008-06-03
May even be easier that that. Check the **Places** menu. (  :oops: overlooked your not using Gnome)
If you change **/etc/fstab** you can run **mount -a **to see the changes go into effect.
Theres been so changes to fstab in Hardy.  probably should take a look at **man fstab**. 

I use a separate backup/data partition, sure come in handy . I think you'll like it.

---

### Post by linuxnovice on 2008-06-04
Hi,
I searched and tried to change my fstab. But I am confused with different kind of info that I see. Besides, that new partition that I created does not even showup when I run df -h. It would really great if you guys could guide me through this.

Thanks.

---

