---
title: "swap space"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by tech_cheetah on 2008-09-24
I have 1GB RAM. I had space problem on my ubuntu partition and so I decided to reduce the swap partition from 2GB to 512MB. Ideally swap space should be twice the RAM size. But due to space crunch, I was left with no other option. Another reason to reduce swap was that I had noticed that the System Monitor shows swap space utilisation 0 % always. 
What I want to know is that is reducing swap partition going to affect the performance in some way ? ( Though I doubt even if this 512MB is going to be ever utilised )

---

### Post by Elfy on 2008-09-24
I have 1GB of each and only touch the swap to any degree when I use gimp or a vm.

If you hibernated then you woin't be able to now as swap has to be equal or greater than ram afaik.

If you have resized your swap the UUID will have changed and fstab will not see it - run 
```
sudo blkid
``` check the UUID against your swap in fstab ```
cat /etc/fstab
``` - if it has changed edit fstab to suit the new UUID ```
gksudo gedit /etc/fstab
``` Once that is done turn the swap on ```
sudo swapon -a
```. Check it is recognised ```
free -m
```

---

### Post by Z2. on 2008-09-25
That has got to be the most concise and yet comprehensive n00b instructions I have yet seen - I'd buy you a beer if you were in my home town

---

### Post by Elfy on 2008-09-25
@Z2. send it psychic mail then - I'm sure I'll get it :)

Glad it helped though.

---

### Post by Nepherte on 2008-09-25
From the Arch wiki: Historically, the general rule for swap partition size was 2x the amount of physical RAM. Over time, as computers have gained ever larger memory capacities, this rule has become increasingly deprecated. Generally, on machines with up to 512MB RAM, the 2x rule is usually quite sufficient. On machines with 1GB RAM, generally a 1x rule is adequate. If you have gratuitous amounts of RAM (more than 1024 MB) it may be possible to completely forgo a swap partition altogether, though this is not recommended.

You shouldn't suffer from much performance loss if you ask me.

---

### Post by aeiah on 2008-09-25
just dont remove the swap all together :p ive been running without a swap for about 4 months now due to sheer laziness. my swap partition was on a hard drive i have since removed and havent bothered to create a new one. it doesnt cause any serious problems but you would notice it on 1GB of ram in certain situations, hehe

---

