---
title: "Odd mounting of partitions"
date: 2011-06-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-06-30
I'm not sure whether this is a OO problem or something in my system.
I'm therefore not sure where to post this - maybe General Help.
I'll see what you guys think first :-)

As you can see from the first screenshot, when I'm running Natty and open gparted the partitions mount in a normal fashion.
However, when I'm running Ocelot and open gparted I get what's shown in the second screenshot, ie strange mount points!
The mounting of the Ocelot system now appears to be via /media - even though I'm booted into Ocelot at the time.
And what's "/,/media/sdb8" all about? That's my Ocelot root partition.

Is this something new, or is something amiss with my system?
Thanks.

---

### Post by lucazade on 2011-06-30
Odd, here are mounted normally and gparted shows them correctly.
Is /etc/fstab ok?

---

### Post by dino99 on 2011-06-30
what catch my attention is your locked partitions, wonder how you makes install

---

### Post by ronacc on 2011-06-30
it looks like in OO the drives shown as /media/XXX had already been mounted while in NN only /  and /Home had been , had you accessed those drives for some reason before running gparted ?

---

### Post by Quackers on 2011-06-30
Oh I just looked. I made a mistake! My Ocelot installation was on sdb10 & sdb11, but I've deleted and added partitions in between. Oh dear, what have I done? The UUID's are correct in /etc/fstab but the /dev/sdb designations are wrong. If I change those will things return to normal?
Here is my /etc/fstab ```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sdb10 during installation
UUID=3623f412-ebb8-451c-aaa9-b7530196248b  /            ext4  errors=remount-ro    0  1  
# /home was on /dev/sdb11 during installation
UUID=12b13c6b-d57d-47ce-92e4-b35b56d36acc  /home        ext4  defaults             0  2  
# swap was on /dev/sdb5 during installation
UUID=1e2ec7b6-946c-4344-90da-73227dfd0514  none         swap  sw                   0  0  
/dev/sdb6                                  /media/sdb6  ext4  defaults             0  0  
/dev/sdb7                                  /media/sdb7  ext4  defaults             0  0  
/dev/sdb8                                  /media/sdb8  ext4  defaults             0  0  
/dev/sdb9                                  /media/sdb9  ext4  defaults             0  0  
```

---

### Post by dino99 on 2011-06-30
you dont need to mount extra partitions but that one you use: /, /home, swap

nothing else, let mountall doing its job, eg "on demand" what it does smootly well

---

### Post by ronacc on 2011-06-30
> **dino99 said:**
> what catch my attention is your locked partitions, wonder how you makes install

drives that are mounted are locked as far as gparted is concerned , it will offer to unmount ( and unlock) them if you try to do something ( repartition/format) to them .

---

### Post by Hedgehog1 on 2011-06-30
If you swap the 4 /dev/sdaX's for UUIDs, that should fix it...

My 0.0. fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=d75b3cb9-37c2-4a53-adb9-f91889a8a3bc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=cb0c7226-150e-45ca-ba5c-2e161dc10f6a none            swap    sw              0       0
# Automount Windows paritions
UUID=EA561004560FCFED                     /media/Area51     ntfs  defaults             0  0  
UUID=5C28DA0E28D9E754                     /media/Area52     ntfs  defaults             0  0 
```

The Hedge

---

### Post by dino99 on 2011-06-30
> **ronacc said:**
> drives that are mounted are locked as far as gparted is concerned , it will offer to unmount ( and unlock) them if you try to do something ( repartition/format) to them .

nothing locked with a minimal fstab on my end

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	2
#Entry for /dev/sdc3 :
UUID=5d8d1ee1-f5af-40a1-a45d-dbc570808523	/home	ext3	defaults,relatime	0	2

#Entry for /dev/sdc2 :
UUID=0a9ca7f0-6eeb-4b21-b70f-670fa600de16	none	swap	sw	0	0

---

### Post by Quackers on 2011-06-30
> **Hedgehog1 said:**
> If you swap the 4 /dev/sdaX's for UUIDs, that should fix it...

The Hedge

The /dev/sdb designations are commented out by default and the UUID's are what's allowing me to boot the system aren't they?
I've changed the /dev/sdb designations and gparted still shows the same - I'm confused.

---

### Post by ronacc on 2011-06-30
your / and /home should be + any drives/partitions you had accessed (on demand) before running gparted .

---

### Post by Quackers on 2011-06-30
> **ronacc said:**
> your / and /home should be + any drives/partitions you had accessed (on demand) before running gparted .

Yes, that's what I would expect - like in my first screenshot when Natty is booted and gparted opened from there.

I don't know what's happened here. 
I'm booted into Ocelot and gparted shows the correct partitions as locked, but it also shows the Natty partitions as locked.

As you say ronacc, surely the 2 Ocelot partitions should have / and /home mount points - not via /media.

---

### Post by Quackers on 2011-06-30
Aha! Problem solved.
I mistook what the Hedgehog had to say!
I have now edited fstab to comment out the 2 lines regarding sdb8 and sdb9. Obviously these lines were to mount partitions which are now gone. As a result of these missing partitions gparted has renamed my remaining partitions and Ocelot is now on sdb8 and sdb9(instead of sdb10 and sdb11), so there is no need for those two lines in fstab any more.

Problem is now solved. Gparted now shows the correct mount points.

Sorry for the confusion. Thanks to all :-)

---

### Post by Hedgehog1 on 2011-06-30
It was nice to help you out for a change.

Lord knows you have come to my rescue more times than I can count!

The Hedge

---

### Post by Quackers on 2011-06-30
Be careful when crossing the road :wink:  I am :-)

---

