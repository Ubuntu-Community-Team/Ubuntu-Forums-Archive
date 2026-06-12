---
title: "Root, Swap, Home sizes?"
date: 2012-05-25
forum: New to Ubuntu
---

### Post by andeh19 on 2012-05-25
Hi everyone, new Ubuntu user here.

I am planning on dualbooting Windows 7 and Ubuntu. I know this question has been asked a lot, but what how big should I make each of the root, swap, and home partitions?

One thing is that I only have about ~20GB for Ubuntu.  I plan to use it for some programming and not a whole lot more.  I also have about 4GB RAM but I will not be using hibernate.  Is 1GB enough for swap?

Any suggestions would be appreciated.

Thanks!

---

### Post by plucky on 2012-05-25
> **andeh19 said:**
> Hi everyone, new Ubuntu user here.

I am planning on dualbooting Windows 7 and Ubuntu. I know this question has been asked a lot, but what how big should I make each of the root, swap, and home partitions?

One thing is that I only have about ~20GB for Ubuntu.  I plan to use it for some programming and not a whole lot more.  I also have about 4GB RAM but I will not be using hibernate.  Is 1GB enough for swap?

Any suggestions would be appreciated.

Thanks!

Welcome to the Forum

If you are only going to use 20GB partition,I would only use a /root and /swap partition and no separate /home partition.That way you can use the whole of the 20GB instead of having wasted space in /root and no space in /home.

If you have more than 2GB of system memory,it is likely you won't be using the /swap partition too much,so I would use a size of 512MB for /swap as you won't be hibernating.

Good Luck

---

### Post by mcduck on 2012-05-25
> **plucky said:**
> Welcome to the Forum

If you are only going to use 20GB partition,I would only use a /root and /swap partition and no separate /home partition.That way you can use the whole of the 20GB instead of having wasted space in /root and no space in /home.

If you have more than 2GB of system memory,it is likely you won't be using the /swap partition too much,so I would use a size of 512MB for /swap as you won't be hibernating.

Good Luck

I agree with the above, but it should probably be noted that /root is not the root filesystem (which would be /), but the root user's home directory. Which you most likely wouldn't want or need to have on a separate partition...

---

### Post by jmore9 on 2012-05-25
Almost all the time when i install linux i only use / and swap partitions.  Makes it way easier to remember where everything is.

---

### Post by mister_playboy on 2012-05-25
My experience with installing a swap partition smaller than the RAM size has been very negative.  The default kernel behavior will see the computer swapping when it doesn't need to and things will grind to a halt because there seems to be an assumption of swap size being greater than/equal to RAM.  Things will be going in and out of swap very slowly while you aren't using more than 50% of your RAM anyway...

With 4GB, I recommend no swap partition.  It will be a waste for 99% of desktop usage.

If you do chose to use swap with a less than 4GB size, I recommend tuning the vm.swappiness parameter to 0 or 5, from the default 60.

---

### Post by grahammechanical on 2012-05-25
Whatever size you decide for your swap partition remember that Ubuntu will install into less than 7GB. An install from the CD will ask for less than 5GB and the install from the DVD will ask for less than 7GB. So 20GB will be plenty but what are you going to do about your data and documents?

Will you be storing them in a partition that is accessible to both Windows and Ubuntu? That would make sense in the opinion of some. Cetainly make regular backups of all data and documents created and stored in the Ubuntu partition because a re-install is sometimes necessary.

Also remember, if you are going to use Ubuntu for a specific purpose then you can make more space in the partition by removing those default programs that are not required. Such as Games.

Regards.

---

### Post by trivialpackets on 2012-05-25
All good advice.  I'd go with one 20 GB partition for /

I normally go with way more swap than I need, but I'm also not normally constrained to 20GB for the whole system.  With that said, and given your use for the partition, I would probably still go with more swap than I need and just have a / and a swap partition.  Maybe like 18/2?  

Enjoy!

---

