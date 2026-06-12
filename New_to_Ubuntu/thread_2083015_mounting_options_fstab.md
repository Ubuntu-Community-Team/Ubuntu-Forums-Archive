---
title: "mounting options fstab"
date: 2012-11-11
forum: New to Ubuntu
---

### Post by doja on 2012-11-11
Hi Ubuntu user,


I have now a dual boot system with  xp and Ubuntu 12.04. During installation of Ubuntu I had 2 connected hard discs to the system and Ubuntu recognized all the partitions without problems. I only had to click in nautilus on the partition and it had been mounted or unmounted. 

I add a 3th internal (SATA) HD which I formatted and  was also able to see in nautilus all 4 partitions (ext4), but couldn't write anything to them. So I created mount points changed fstab (options- default) and everything is working.

The small but is that Ubuntu automatically mount all 4 partitions and 4 icons appear in launcher (what I don't like so much). I would like to change the options so that I can mount and unmount this partitions per click  in nautilus. 

A copied  line  from fstab  with the right options will be great.

thanks
doja

---

### Post by ajgreeny on 2012-11-11
I believe you have two options at least, possibly more.

[LIST=1]
[*]You can change the mount point of the partitions to /mnt/*folder* instead of /media/*folder* or you can
[*]right click on the icons/launchers in the launchbar and choose to remove (or unlock, I don't use unity and can't remember)
[/LIST]
I am pretty sure the partitions will still show in nautilus >Places wherever they are mounted, but you may need to double check that.

---

### Post by LiamOS on 2012-11-11
Changing the mount location to /mnt/ should do the trick as far as getting them off your desktop goes, I believe.
You could also consider adding the noauto option in fstab.

---

### Post by doja on 2012-11-11
shifting the mount points to /mnt solved the problem.

The icons in launcher don't appear anymore but they are not listed in nautilus under devices either (= on the left hand side  in nautilus). But I can found them in nautilus under /mnt. This is sufficient, maybe even better considering 3 HD  each with 4 partitions.

I tested the 'noauto' option in fstab before, but because the volumes didn't appear in nautilus under devices I thought that I'm doing something wrong.

thanks both of you,
doja

---

### Post by LiamOS on 2012-11-11
If finding /mnt is a bit of a pain, you could also make a symlink in your home folder to /mnt.
Opening your terminal and doing a 
% ln -sv /mnt mnt/
should do the job.

---

### Post by doja on 2012-11-12
I wondered about the different behavior between the HD's that where connected before and after the Ubuntu installation, so that I additionally looked on the internet and played around little bit. 

I looked after the mount points for the HD's connected before the installation and found out that they are under /media/...  But they are visible only when the partitions are mounted. I also wondered why they don't appear in the fstab.

So I removed the mount points of the additional HD and commented out the relevant lines in fstab.  Now the new HD behaviors like the old ones. I see the  partitions under devices in nautilus where I can mount and unmount them per mouse click. If they are mounted they appear in launcher. It seems to be ok now.

The point why I started create the mount points was that I couldn't make a new   folder in the new partitions and wasn't allowed (as far I know) to change the owner rights  for them in terminal before creating the mount points. After that I could change the writing rights. 

But because I'm new in Linux maybe I did something wrong by trying change the writing rights for the new HD (maybe forget sudo) and then tried to overcome this mistake. I can not explain it otherwise.  

Learning is a process :-)
doja

---

### Post by doja on 2012-12-24
After new partitioning I get the same problem that I couldn't change the owner rights.

But now I found the problem. The point was that one can not change the owner rights of a partition that is not mounted.

The mount point of an internal HDD appear under media only if the partition is mounted.

-> 1. mount the partition ->2. change the owner rights of the partition.

---

