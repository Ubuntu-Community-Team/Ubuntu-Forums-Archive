---
title: "no swap area"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by MaWiSo on 2012-04-30
I installed ubuntu without assigning a swap area 


can i fix this now or i have to reinstall ubuntu ????

---

### Post by strask on 2012-04-30
You can create a swap file in the filesystem without reinstalling anything. You would use the dd command to create the file, the mkswap command to initialize it, and the swapon command to start using it.

So for example:```

sudo dd if=/dev/zero of=/swapfile bs=1024 count=2097152
sudo mkswap /swapfile
sudo swapon /swapfile
```

This would make a swap area of 2gb in the file /swapfile on your root filesystem, format it, and turn it on.

To have it turn on automatically at boot time you would need to add it to /etc/fstab, a line like this would work for the above:```

/swapfile        none        swap        sw        0        0
```

The only thing to worry about is if you need to be able to use the hibernate function; that requires a swap partition, and won't work with a swap file like I describe.

---

### Post by MaWiSo on 2012-04-30
what if i need the hibernate function ??


I already have a 10 GB free space on my hard disk for the swap area .
how to use them ?

---

### Post by plucky on 2012-04-30
> **MaWiSo said:**
> what if i need the hibernate function ??


I already have a 10 GB free space on my hard disk for the swap area .
how to use them ?

See [SwapFaq](https://help.ubuntu.com/community/SwapFaq) to enable your swap partition.10GB seems quite large.

Swap partition needs to be at least the size of your memory to hibernate.

Good Luck

---

