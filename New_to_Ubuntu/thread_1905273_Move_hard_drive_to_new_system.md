---
title: "Move hard drive to new system"
date: 2012-01-06
forum: New to Ubuntu
---

### Post by techman.chan on 2012-01-06
Bit of noob to unbuntu and followed a guide years ago to setup this basic file server. Since then it works and never wanted to touch it until now.

I would like to know if I can move my current storage drives (3 -2tb drives from my ubuntu 8.04 lts server to a new build ubuntu lts server without loss of data or screw them up.

Basically I want to unplug current drives and move them and plug them into new system add them to fstab file them mount them and add to the samba config file. All without losing my important data. How or can I do this????

Currently the drives are formatted as ntfs and setup with samba on a headless server.

---

### Post by bluexrider on 2012-01-06
If they are just data drives you can do just that.

The drive containing the actual OS will have some modifications. ie: reconfigure sda /boot for you new OS.

This should not be a hard issue to resolve. Fairly straight forward. 

Loss of data occurs when reformatting or partitioning the drive itself.

---

### Post by Basher101 on 2012-01-06
as long as you do [COLOR="Red"]NOT[/COLOR]:

format the drives
throw them at a wall (or give them shockwaves of any kind)
throw them into water
or unplug while they are running

you should have absoluteley no data loss at all.
everything else would be hard drive failure..which is eminent at some point

---

### Post by rsvancara on 2012-01-07
I would also consider getting some information about those three drives such as running 

blkid /dev/sdxx

against each drive to obtain their UUID.  

Also look in the /etc/fstab and see how they are mounted and write it down somewhere so you can install the drives exactly how they were in the current system.  

Finally, I would recommend a good backup.  Even though this is fairly straight forward, there is still room for error.

Best of luck!

---

