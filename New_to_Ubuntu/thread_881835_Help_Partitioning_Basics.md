---
title: "Help Partitioning Basics"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by Perastikos on 2008-08-06
Hi!

I'm going to install ubuntu 8.04.1 in my desktop PC. My PC consists of a 400GB hard disk and 2GB RAM. What about the partitions and the right size of each partition?

---

### Post by bodhi.zazen on 2008-08-06
The Tips and tutorials section is not for support questions.

partitioning is an art and there is not single right or wrong way.

Typically I advise a 5-10 Gb partition for root ( / )

Swap + ram X 1 , max 1 gb, swap = RAM if you have a laptop and wish to suspend / hibernate.

The rest a separate data partition.

---

### Post by hyper_ch on 2008-08-06
I'd use 20GB as root ;) just to be sure :)

---

### Post by hashimoto on 2008-08-06
[QUOTE=Perastikos;5534232What about the partitions and the right size of each partition?[/QUOTE]

Maybe these links will help you:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.easy-ubuntu-linux.com/ubuntu-installation-606-9.html](http://www.easy-ubuntu-linux.com/ubuntu-installation-606-9.html)

---

### Post by cgkades on 2008-08-06
> **hyper_ch said:**
> I'd use 20GB as root ;) just to be sure :)

That should be pretty good. I used auto partition for a solaris box I have. Never again. Give your self some room to grow with apps. 20 Gigs plus is good if you have the space.

---

### Post by jbrown96 on 2008-08-06
I've never had my system use more than 10GB. I would format the following way:
2GB Swap
12GB ReiserFS mounted as /
rest of the hard drive I would use as /home/ as either ReiserFS or XFS. ReiserFS is very fast for small files. XFS does very well with large files (i.e. videos). Note that you cannot use XFS as the root partition (maybe JFS too).

If you think that you may be trying out multiple distros, I would make another partition that is 10GB that is unused. That way you can try other distros without doing any formatting.

---

### Post by hyper_ch on 2008-08-06
well, if you rip a dvd it will save the data temporarily in /tmp and if you run out of diskspace you have a problem... that's why I say 20gb

---

### Post by kansasnoob on 2008-08-06
> **hyper_ch said:**
> well, if you rip a dvd it will save the data temporarily in /tmp and if you run out of diskspace you have a problem... that's why I say 20gb

I agree. I've recently been editing old home videos (I should perhaps say trying to edit videos:redface:) and it gets quite resource hungry!

---

