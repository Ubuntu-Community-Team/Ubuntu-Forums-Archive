---
title: "Swap partition?"
date: 2013-03-24
forum: New to Ubuntu
---

### Post by mutorola1986 on 2013-03-24
Hi, I'm new for this, I installing ubuntu 12.10 during install its say something swap partition. Is it necsessary and if i creat this what size should i make for swap partition.

Sorry for bad English, I use dictionary for this and Google translate:confused::confused::confused:

---

### Post by mikewhatever on 2013-03-24
It is not necessary, but if you choose to create it, it should be about the size of RAM. In other words, if the machine has 1GB of RAM, a 1024MB swap should be enough.

---

### Post by SlothX on 2013-03-24
Swap should be twice the amount of RAM.

If RAM is 2GB, then swap should be 4GB.

Creating swap is recommended because when you hibernate your PC, the data gets stored in swap.

[You can read more about swap in the Ubuntu community doc]("https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need").

---

### Post by drpjkurian on 2013-03-24
i advise you to create a swap of double the size of your RAM

---

### Post by mutorola1986 on 2013-03-24
OK, Thank guys

---

### Post by mikewhatever on 2013-03-24
> **SlothX said:**
> Swap should be twice the amount of RAM.

If RAM is 2GB, then swap should be 4GB.

Creating swap is recommended because when you hibernate your PC, the data gets stored in swap.

[You can read more about swap in the Ubuntu community doc]("https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need").

Respectfully, I beg to disagree. 4GB of swap is usually a waist of space. What on earth is one going to do with 4GB of swap? ...and what if there is 8GB of RAM, ...or how about 16? The "twice the amount of RAM" rule is an old relic from two decades ago.
Hibernating is disabled in Ubuntu, that is, there is no hibernate button anywhere.

---

### Post by sartorius on 2013-03-24
> **mikewhatever said:**
> 
Hibernating is disabled in Ubuntu, that is, there is no hibernate button anywhere.

Then I'm a little confused.  Isn't there a hibernate option on the pull-down menu in the upper right?  (This is from memory...I'm considering reinstalling Ubuntu and am wondering if I should create a /swap, its position on the disk, etc.)

---

### Post by mikewhatever on 2013-03-26
If you plan on using it, then do create a swap partition just over the size of RAM.
Hibernation has been disabled since 12.04, because the developers deemed it buggy. So, there is no hibernate in menu that menu by default, but, of cause, it is easy to re-enable.
[http://askubuntu.com/questions/94754/how-to-enable-hibernation](http://askubuntu.com/questions/94754/how-to-enable-hibernation)

---

### Post by schragge on 2013-03-26
+1
For hibernation to work a swap partition of the size slightly more than your RAM size is needed. If you have 4GB RAM, 4.1GB swap space will be enough to store all RAM contents during hibernation.

---

### Post by DuckHook on 2013-03-26
Just to muddy the waters further, if you don't intend to re-enable hibernation, then swap of 1x is still overkill in most cases. Eg. If you have 8GB of Ram installed, it makes little sense to make a swap partition of, say, 9 GB. Once system starts swapping as little as 1 or 2 GB to disk, performance will get so sluggish that most people will throw their hands up and do something about it (i.e. close down some apps, add more memory, etc). Of course, if your system only has 1 GB of RAM, then a swap of minimally 1GB is still recommended. Here is my rule of thumb:

Up to 4 GB of RAM: Swap = 1 GB
4 - 8 GB RAM: Swap = 2 GB
Over 8 GB RAM: Swap = 4 GB

The 3 big exceptions are:

1. If hibernating, then you need swap at least equal to amount of RAM in GiB (not just GB).
2. If box is used as a server, then a large swap partition for safety margin is advisable.
3. If running memory-intensive tasks like multiple VMs or A/V work, then again, larger swap for safety margin is advisable.

---

