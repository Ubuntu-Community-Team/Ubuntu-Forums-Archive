---
title: "swap on second hard drive"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by bigmonmulgrew on 2008-08-08
Hi I have a western digital raptor 74 GB
It is split 22GB for XP32
22GB for XP64
2GB for a swap and the rest for Ubuntu.

As the drive is so small I'd like to reclaim the swap file if im at no loss.
I have a second hard drive which is just used for storage.

Would it be suitable to put the swap on the second drive.
The second drive is reasonably fast but no where near up to raptor standards. Will I lose performance from moving it.

---

### Post by Elfy on 2008-08-08
First thing is do you need to have that much swap. But I can't imagine it would make a great deal of difference. How much of the swap do you use during the day - ```
free -m
``` will give you an idea of it's use.

---

### Post by sdennie on 2008-08-08
It should be fine to put the swap on a second drive.  Once you create the swap partition just run:

```

sudo blkid

```

To find the new UUID for the swap partition and modify /etc/fstab to reflect that new information.  After that change, you will probably also need to run:

```

swapon -a

```

And then to verify that everything worked:

```

free -m

```

---

### Post by bigmonmulgrew on 2008-08-09
> **forestpixie said:**
> First thing is do you need to have that much swap. But I can't imagine it would make a great deal of difference. How much of the swap do you use during the day - ```
free -m
``` will give you an idea of it's use.

ah cheers didnt know how to check usage. Im using 500ish /2000 ram and no swap at all.
I've only a web browser and add/remove open but thats not bad

---

### Post by eightmillion on 2008-08-09
[This]("https://help.ubuntu.com/community/SwapFaq") is the very handy Ubuntu swap FAQ. It should be noted that you can mount a swap file.

---

### Post by rockerphil on 2008-08-09
yes, it's very possible and quite useful to put a swap partition on your second hard drive (at least in my particular case) i personally had the same problem with my system. my primary HDD is only 8 GB, so i need as much of that space as possible. so i simply used the Gparted live CD to delete the swap partition from my primary HDD, then created a 1.5 GB swap partition on my 2nd HDD which is 40 GB (much larger than my primary) and did a bit of editing to my fstab file, thus giving me all of my primary HDD space to use for Ubuntu. hope this helps,

Phil

---

