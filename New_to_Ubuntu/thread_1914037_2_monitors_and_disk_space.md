---
title: "2 monitors and disk space"
date: 2012-01-23
forum: New to Ubuntu
---

### Post by Sup3I2Son1c on 2012-01-23
Hi everyone.
I'm new to ubuntu, and linux generally (been a windows user up until now.)
I installed ubuntu 11.10 and I can't manage to detect my other monitor.
I have 2 monitors (samsung syncmaster 245b and syncmaster SA350).
245b is connected to primary GPU output via DVI cable and I have output on this monitor. SA350 is connected to secondary GPU output via HDMI cable and I have no output on this monitor. Ubuntu doesnt recognize it in system settings/display, just one current monitor (245b) "recognized" as unknown in native resolution 1920x1200.
My GPU is nvidia GTX260, ubuntu installed drivers while OS installation took place. I didn't install any additional drivers.

The other thing is, I misscalculated disk space distribution, or I think I did, while partitioning right before installation of the OS. I gave 3 GB to root (now I see that's not enough), 4 GB to swap and 57 GB to /usr. I have other disks and partitions but they're all used and I need that data. So my question is, how can I make that Ubuntu software center that I like so much to install apps to /usr partition instead of root, 'couse my root is full now and I just started downloading apps.

If not possible than what's Your opinion on disk space quantity for root, swap and /usr partitions? I have 8 GB RAM and I use various programs for graphic design, 3D modeling, sound editing and similar.

---

### Post by partloer on 2012-01-24
Welcome to Ubuntu forums!

Monitor
What you mean primary GPU do you mean motherboard or do you have two GPUs?

I know that I had problems with the Ubuntu open source drives in that it wouldn't display both of my monitors at high resolution what I ended up doing is install the manufacture drivers and that got it to work so that might be one option.  I see that nVidia has Linux drivers for the GTX260.

Partition
The general rule of thumb for swap is 2x[size of RAM] so in your case 8GB of RAM = 16GB of swap.  

Now to re-size the partitions you can use gparted this is the partition editor from the liveCD (System->Administration).  So you would have to boot up the liveCD make the partition changes then save.  But first always backup your data.  

As for partition setup I just split up swap and root but I also don't save much data to my hard drive so I don't have to worry about space requirements.

---

### Post by Paqman on 2012-01-24
> **Sup3I2Son1c said:**
> I didn't install any additional drivers.


That's likely to be your problem. Go ahead and install the driver that Additional Drivers suggests.

---

