---
title: "Re-partitioning advice wanted"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by t0p on 2008-07-25
I'm planning to re-partition my hard disk to give me a separate /home partition.  All I want is some advice: my computer has a 20 GB hard disk.  How much memory would you suggest I use for /home? How much for /?

---

### Post by billgoldberg on 2008-07-25
> **t0p said:**
> I'm planning to re-partition my hard disk to give me a separate /home partition.  All I want is some advice: my computer has a 20 GB hard disk.  How much memory would you suggest I use for /home? How much for /?

I would use 1gb for /, 1gb for /swap and the rest for /home.

---

### Post by arpanaut on 2008-07-25
I don't know about 1gb for / 
I just did an install on my laptop and after without much configuration or adding of programs the root partition was at 2.8 gb...
So plan accordingly

---

### Post by gmjs on 2008-07-25
Not wishing to be awkward, personally I'd leave a bit more space for the root partition. Currently, I'm using 8.6GB at / (excluding home directories), and 4.8GB in /home.

Maybe 

/     5GB
/home 14GB
/swap 1GB

Any suggestions welcome though.

---

### Post by unutbu on 2008-07-25
To figure out how much space you'll need for /,
you could run the following:

To see how much space is currently being used by / (with /home):
```
df -H
```

To see how much space is being used by /home:
```
sudo du /home -sh
```

Subtract, and you'll have an estimate of how much space you'll need for /.

---

### Post by arpanaut on 2008-07-25
> **gmjs said:**
> Not wishing to be awkward, personally I'd leave a bit more space for the root partition. Currently, I'm using 8.6GB at / (excluding home directories), and 4.8GB in /home.

Maybe 

/     5GB
/home 14GB
/swap 1GB

Any suggestions welcome though.

Exactly what I was thinking.

---

### Post by bankg3 on 2008-07-25
> **gmjs said:**
> Not wishing to be awkward, personally I'd leave a bit more space for the root partition. Currently, I'm using 8.6GB at / (excluding home directories), and 4.8GB in /home.

Maybe 

/     5GB
/home 14GB
/swap 1GB

Any suggestions welcome though.

I agree, 5GB gives you enough for expansion etc, and through all my installations I have never needed more that this, but commonly I need more than 1 GB.

---

