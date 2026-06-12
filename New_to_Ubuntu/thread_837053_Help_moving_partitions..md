---
title: "Help moving partitions."
date: 2008-06-22
forum: New to Ubuntu
---

### Post by graynada on 2008-06-22
It is all my own fault because a rushed my installation but I wonder if anyone could help me with a step by step guide to sort this out;

I have installed my system (8.04) as follows on two 250 Gb drives.

Drive 1: 2G Swap; 25G /; 25G /opt; 50G /home; 147G /share; 1G /boot
Drive 1: 2G Swap; 25G /; 25G /opt; 50G /home; 147G /share; 1G not used.

I have used software raid 1 for the /, /opt, /home and /share as follows

md0 /; md1 /opt; md2 /home; md3 /share

Having done this and installed all the software I want and got the system set up how I want I have realised my mistake, I really wanted/needed the /usr directory on a separate partition not the /opt.

Can I move the /opt (which is virtually empty) back into the / partition and move the /usr into its place?

Failing this can I move /opt back into the / partition and merge the /opt partion into the / partition to reclaim the 25G I am essentially not using?

Thanks in advance

Graham

---

### Post by geirha on 2008-06-22
25G for / and /usr is plenty enough I should think. I use 6GiB for those two in total, and I've installed alot of programs. Having it roomy in / and /usr is not at all a bad thing though.

you may simply copy the content of /usr to the partition mounted at /opt
(if you have anything in /opt except lost+found, move it away first)
```
sudo cp -a /usr/* /opt/
```
Then edit /etc/fstab and have the partition that mounts to /opt, mount to /usr instead. After a reboot / and /usr should be seperate, and /opt should be empty.

However, after this you'll have two copies of /usr, one on / and one on a different partition mounted at /usr. It does not produce a collision or anything, the usr-dir on / is just hidden, and everything you see in /usr is on the other partition. 

The easiest way to remove your old usr-dir, is probably just to boot the ubuntu cd, mount your / partition to /media/disk and move the usr to usr.backup. And don't forget to create an empty /usr/ in its place. 
```

sudo mv /media/disk/usr media/disk/usr.backup
sudo mkdir /media/disk/usr

```

When you boot back in to your regular system, and see that everything is as it should be, you can remove /usr.backup at your own discretion

---

### Post by fahadsadah on 2008-06-22
Do the following steps from a LiveCD:

Back up /usr and /opt somewhere.
Edit /etc/fstab, and change /opt to /usr.
Mount this disk, and copy the /usr backup to it.
Make a directory called /opt.
Copy the /opt backup here.
Delete the backups.

EDIT: Whoops, I was beaten to it. Anyway, this method is guaranteed to work.

---

### Post by graynada on 2008-06-27
Many thanks for you replys. I did wonder if it were as simple as that but being a newish (but very enthusiastic) covert I didn't want to mess it up.

All sorted now and thanks again.

---

