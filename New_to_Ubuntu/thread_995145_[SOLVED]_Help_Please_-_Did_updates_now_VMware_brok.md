---
title: "[SOLVED] Help Please - Did updates now VMware broken"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by luckylucky on 2008-11-27
I use ubuntu 8.04.  I rarely do updates as I often find something doesn't work properly afterwards, and have grown scared of the updates.

I did a large update (large because there were tons of stuff to update since not doing it for months) and now VMware doesn't work.  Yeah yeah, of course I rebooted and all (repeatedly)

Before updates vmware = perfect
after updates vmware = broken

Now when I try to run vmware it looks for about 5 seconds like it is loading, but then poof nothing.  It's like I shut down the program or something as nothing is there; no task bar item, no window, nothing.  I keep trying to launch vmware but nothing.

How can I get this fixed now?  This is a crucial item for my needs, and thus my computer is currently partially useless.

---

### Post by ibuclaw on 2008-11-27
I think installing **dkms** will fix future breaks with compiled kernel modules.
```
sudo apt-get install dkms
```

But to fix the problem now, I think you run the vmware-config.pl again.
```
sudo vmware-config.pl
```
And press Enter throughout it.

Regards
Iain

---

### Post by luckylucky on 2008-11-27
Thank you very much... it worked!  :)

---

