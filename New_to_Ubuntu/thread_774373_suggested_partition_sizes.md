---
title: "suggested partition sizes"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by eko291 on 2008-04-29
I am about to make the switch from running under vmware to running on a seperate drive from my windows install. Currently, I have a free 300GB drive.  What would everyone suggest for partition sizes?  I would guess I should go with /swp, /(root), and a seperate /home.

Mark

---

### Post by aheckler on 2008-04-29
/ = 15 GB maximum, depends how many apps you want to install
Swap = Depends on your RAM, but generally no more then 1 or 2 GB
/home = the rest

---

### Post by kestrel1 on 2008-04-29
I would let Ubuntu decide.

---

### Post by billgoldberg on 2008-04-29
Let ubuntu take the whole drive.

Unless you want a seperate /home

Then I would give / around 10gb, 2 gb swap and the rest to /home

---

### Post by defmomo on 2008-04-29
How big is your current drive? And would you be willing to format or resize your current partitions?
If not, you could simply mount the whole drive as a /data partition, separate from your home partition, so you can use it to hold backups or data in case you install other distros, or switch OS, or anything else.
One thing that can be real helpful, is having two swap partitions on different drives, configure ubuntu to use them both at the same time, that would practically double the speed of your swap.
You can do this by editing the /etc/fstab file and changing the swap lines, for example:
```

#/dev/sda6                                                                                                                                                                                      
UUID=becfb61a-260a-4678-ae90-f0b8554517bf none swap sw 0 0
#/dev/sdb1                                                                                                                                                                                      
UUID=9eb31ad9-0e6f-43fe-84f3-c2978c714fc8 none swap sw 0 0

```
and adding the same priority flags to both swaps:[pri=10], underlined here:
```

#/dev/sda6                                                                                                                                                                                      
UUID=becfb61a-260a-4678-ae90-f0b8554517bf none swap sw,_pri=10_ 0 0
#/dev/sdb1                                                                                                                                                                                      
UUID=9eb31ad9-0e6f-43fe-84f3-c2978c714fc8 none swap sw,_pri=10_ 0 0

```
Oh and place the swap partition at edge of the hard drive, as it should make it faster.

---

### Post by T-Virus on 2008-04-29
I suggest having /swap twice as you have RAM (as an example I have 2GB of ram and 4GB of /swap) and that's in case if you can allow yourself that!

Now with / partition... I use programs which take some place like - Maya. So that's actually for you to decide. I would say 20gb is more than enough.

And leave the rest for /home. Well, that's just my opinion.

---

### Post by defmomo on 2008-04-29
OOps! sorry, I didn't read your post fully! Since you will only use the 300GB drive, I suggest a maximum of 40GB for /, a separate /var if you will run a server, and a separate /tmp, just for added security, and /home gets the remaining space. My previous advice about the swap partition being at the edge of the drive is still relevant, but I would like to add that you should partition the whole drive as a logical volume, so you can resize partitions on the fly from there on.
Although consider that the /boot [COLOR="Red"]MUST[/COLOR] be located on a primary partition.

---

### Post by eko291 on 2008-04-29
thanks for all the suggestions!

---

