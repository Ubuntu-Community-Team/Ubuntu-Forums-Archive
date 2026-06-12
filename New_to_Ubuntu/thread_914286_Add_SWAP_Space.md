---
title: "Add SWAP Space"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by Ludwig9 on 2008-09-08
I recently did a partitioned installation of Ubuntu Hardy, but gave it too little swap space. I have 1 GB of RAM. I gave by mistake only 2 MB to swap when I should have (correct me if I am wrong) given it 2000 MB. The machine changed the 2MB automatically to 8MB. But the computer is not working well with just 8MB. Do I need to do a reinstall to create more SWAP? Is there some other way to do it? I plan to install the new Ubuntu due out on 9/16. I can wait till then, but would rather fix Hardy now.

---

### Post by Sealbhach on 2008-09-08
I don't think the low performance is necessarily due to a small swap space. 

I think that swap is only used if your RAM is completely used up - how much RAM are you using?

You can find out by looking at System/Administration/System Monitor


.

---

### Post by kjohansen on 2008-09-08
You can boot from the LiveCD and use gparted to change the partition sizes.

Backup your data before playing with the partitions.

---

### Post by Ludwig9 on 2008-09-08
> **Sealbhach said:**
> I don't think the low performance is necessarily due to a small swap space. 

I think that swap is only used if your RAM is completely used up - how much RAM are you using?

You can find out by looking at System/Administration/System Monitor


.

It says about 225 MiB (22.0 %) of 1009 MiB; Swap is 0 bytes (0.0%) of 7.8 MiB. 
(I'm in Windoze right now; but this is what it said before when I checked it.

---

### Post by Ludwig9 on 2008-09-08
> **kjohansen said:**
> You can boot from the LiveCD and use gparted to change the partition sizes.

Backup your data before playing with the partitions.

Can you give me link to tell me more about "gparted"? I'm unfamiliar with it.

---

### Post by Sef on 2008-09-08
> I have 1 GB of RAM. I gave by mistake only 2 MB to swap when I should have (correct me if I am wrong) given it 2000 MB. 

With 1 GB ram or more, you need only 1 GB (1000 MB) swap.  If you do need more swap, then get more ram.

---

### Post by kansasnoob on 2008-09-08
Could you post a screenshot of Gparted?

With a fresh install you may have to install it:

```
sudo apt-get install gparted
```

Then you'll find it in System > Administration > Partition Editor. Mine for example:

[ATTACH]84628[/ATTACH]

To post a screenshot just go to Applications > Accessories > Take Screenshot and then use the paperclip looking thingy to attach it here.

---

### Post by kansasnoob on 2008-09-08
> **Ludwig9 said:**
> Can you give me link to tell me more about "gparted"? I'm unfamiliar with it.

Don't try making any changes in gparted yet! PLEASE!

---

### Post by Ludwig9 on 2008-09-08
> **Sef said:**
> With 1 GB ram or more, you need only 1 GB (1000 MB) swap.  If you do need more swap, then get more ram.
OK, but it says in [https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html)  
"Swap partition - this need only be twice the size of your memory"

"You will need to make it (sc. swap space) double the size of your installed memory."

BTW, this is a new (used) machine I'm using, with almost nothing on it. I have used Hardy before without the little problems I'm having now. I have no basis for thinking that my problems stem from insufficient swap space other than statements like those sited above. In other words, I'm just guessing. Thanks.

---

### Post by Ludwig9 on 2008-09-08
> **kansasnoob said:**
> Could you post a screenshot of Gparted?

With a fresh install you may have to install it:

```
sudo apt-get install gparted
```

Then you'll find it in System > Administration > Partition Editor. Mine for example:

[ATTACH]84628[/ATTACH]

To post a screenshot just go to Applications > Accessories > Take Screenshot and then use the paperclip looking thingy to attach it here.
I've got to go eat, but I try this tomorrow or later tonight. Thanks.

---

### Post by unutbu on 2008-09-09
I think the suggestion that "swap should equal twice the amount of physical RAM" should be taken as a suggestion but not as a hard-and-fast rule.

Consider this thought-experiment: You have a working system. You add another 1GB of physical RAM. Why should adding RAM require more swap? 

The only situation that I know of where adding RAM may require more swap is if you are trying to hibernate your system. Then the RAM is written entirely to swap space. So to hibernate, you do need your swap space to be at least as large as your RAM.

Here is a way to test if you need more swap space:
You can make a swap file (instead of resizing your swap partition). Except for the fact that it is not in a partition of its own, the swap file acts just like a swap partition. 

To make a swap file:
```
dd if=/dev/zero of=/swapfile bs=1024k count=2000      # 2GB swapfile
mkswap /swapfile
swapon /swapfile
```

To make the swapfile activated at boot-time:
```
gksu gedit /etc/fstab
```
add this line:```

/swapfile       none    swap    sw      0       0

```
To turn off a swap file and reclaim the hard drive space:```

swapoff /swapfile
sudo rm /swapfile

```

---

### Post by Ludwig9 on 2008-09-09
> **kansasnoob said:**
> Could you post a screenshot of Gparted?

With a fresh install you may have to install it:

```
sudo apt-get install gparted
```

Then you'll find it in System > Administration > Partition Editor. Mine for example:

[ATTACH]84628[/ATTACH]

To post a screenshot just go to Applications > Accessories > Take Screenshot and then use the paperclip looking thingy to attach it here.

Here is the screenshot. Thanks for explaining how to take one.

---

