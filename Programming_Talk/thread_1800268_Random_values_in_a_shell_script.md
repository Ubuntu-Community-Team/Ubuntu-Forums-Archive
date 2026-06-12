---
title: "Random values in a shell script"
date: 2011-07-08
forum: Programming Talk
---

### Post by Heru-Ur on 2011-07-08
Hello,

I am trying to write a shell script that will generate a random mac address on boot. I however do not know how to go about solving the Random part. I would like to use a list/array of all the valid choices for a mac address, i.e. 0-9 and a-f. I am lost on how to do make that happen. Any help would be appreciated.

Thanks

---

### Post by gmargo on 2011-07-08
You could use the $RANDOM variable inside a **bash(1)** script.  But it's easy in perl:

Here's a perl 1-liner that will generate a man address:
```

$ perl -e 'sub x(){int(rand(256))};printf "%02x:%02x:%02x:%02x:%02x:%02x\n", x(),x(),x(),x(),x(),x()'
7f:a8:ea:e5:b0:5d

```

---

