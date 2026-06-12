---
title: "Setting up a swap file?"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by Nitrius on 2008-08-17
Following this guide: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

According to it, i should have my RAM*2 i got 4096(4GB ram), so i should get a swap file of 8192MB. Should i then change all the "512" parts in that guide with "8192" instead? or?

---

### Post by dreadmeat on 2008-08-17
i have 1.5GB or ddr ram strapped to a p4 @ 3GHZ
i set my swap to 100**MB** a couple of weeks ago, no explosions yet.
in fact even @ 100% cpu i'm only using 38% of my swap.
with that amount of ram you'll never use the swap at all i reckon.

ymmv

---

### Post by hyper_ch on 2008-08-17
> **Nitrius said:**
> Following this guide: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

According to it, i should have my RAM*2 i got 4096(4GB ram), so i should get a swap file of 8192MB. Should i then change all the "512" parts in that guide with "8192" instead? or?

Do you have Ubuntu 64bit installed?

---

### Post by Nitrius on 2008-08-17
Yes, am using Ubuntu 64bit.

---

### Post by Elfy on 2008-08-17
Do you hibernate - if so I think that RAM=swap - if you don't then it's unlikley you'd use the swap unless you use memory intensive apps. You might like more if you use virtual machines a lot.

But I have only used about 50Mb of my swap with 1.3Gb RAM - except when I run a vm. I assume you have a 64bit processor.

If you don't then I would suggest a small swap - it's better to have some than none I would think, especially if hdd spcae isn't a problem

---

### Post by Sef on 2008-08-17
> According to it, i should have my RAM*2 i got 4096(4GB ram), so i should get a swap file of 8192MB. Should i then change all the "512" parts in that guide with "8192" instead? or?

2 times ram does not apply above 512 mb.  The most you should have would be 1 GB.

---

### Post by Canis familiaris on 2008-08-17
I think you should have 4096MB + 512MB = 4608MB of SWAP.

Swap space should be Double the Amount of RAM OR RAM + 512MB whichever is lower.

---

### Post by dreadmeat on 2008-08-17
[interesting LQ forum thread]("http://www.linuxquestions.org/questions/linux-general-1/swap-file-or-swap-space-662980/") :arrow:

---

### Post by drboontu on 2008-08-17
Hi,

Interesting reading here:
[http://www.brunolinux.com/06-Fine_Tuning_Your_System/Swappiness.html](http://www.brunolinux.com/06-Fine_Tuning_Your_System/Swappiness.html)

On one machine with 1 gig ram and 512mb swap I use settings

vm.swappiness=10

No problems, (desktop system).

Cheers,

---

### Post by Nitrius on 2008-08-17
Got a 64bit cpu yes, Q6600, and i dont use hibernate.

So i should just follow the guide i posted in the topic, to make myself a swap file at 512mb ram? I would rather have a swap file than an swap partition.


Edit: The reason for making this thread, is because when i used the guided installation metode on ubuntu it made my a swap partition of 11gb, which seems to be quite a lot..

---

### Post by Sef on 2008-08-17
> Edit: The reason for making this thread, is because when i used the guided installation metode on ubuntu it made my a swap partition of 11gb, which seems to be quite a lot..

That is 10 GB too much.  I just manually partition my hard drive, but that is not for everyone.

---

### Post by Nitrius on 2008-08-17
Yea, I've manually partitioned my hdd as well, though i did that in vista, since am dual booting. And since i don't have a lot of experience with linux yet, i choose guided when i installed ubuntu the first time.

So my idea now, is to install ubuntu again without swap, and then use the guide in the first post to apply a swap file, which according to the guide is at 512mb. Will that work?

---

### Post by drboontu on 2008-08-17
Hi,

11gb is very large...

A lot depends on what you plan to use the computer for.

Editing Audio/Video for example.

512mb should be fine for a Desktop computer,
If you want to be safe make it 1 gig. It's still 10gb less.

Cheers,

---

### Post by Nitrius on 2008-08-17
If i want to set it to 1024mb, how do i do that then? Am thinking on the swap file guide i posted in my first post here, should i just change all the "512" entries with "1024" instead?

Like this?
```

sudo dd if=/dev/zero of=/mnt/1024Mb.swap bs=1M count=1024
sudo mkswap /mnt/1024Mb.swap
sudo swapon /mnt/1024Mb.swap
sudo gedit /etc/fstab

```
and add this line at the end of the file:
```
/mnt/1024Mb.swap  none  swap  sw  0 0
```


Don't have any plans on what am gonna use the computer for, this is mainly just me trying and experimenting with linux/ubuntu. So i don't mind formatting the OS for the time being.

---

### Post by Paqman on 2008-08-17
If you take a look at System Monitor you can see how much swap you're actually using (there's a good panel applet for this, too)

In your case i'd be really surpised if you were using it much.

---

