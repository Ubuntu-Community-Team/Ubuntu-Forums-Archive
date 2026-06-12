---
title: "How do I upgrade old partition that can't boot?"
date: 2014-07-13
forum: New to Ubuntu
---

### Post by Wiking on 2014-07-13
I was purging some old kernels from my /boot partition and I guess I must have deleted something important because I can't boot into my kubuntu partition.

I downloaded 14.04LTS to boot live into the /home and /  partitions. 

How can I upgrade the old /  and /home partition so that the live CD doesn't overwrite anything just upgrades and updates the old partitions?

thanks

---

### Post by deadflowr on 2014-07-13
How is you partition scheme setup?

And how did you clean it?
(did you  simply delete stuff/files, or remove with apt, or a package manager, like synaptic?)

---

### Post by Wiking on 2014-07-13
partition setup is:

/windows
/boot
/swap
/kubuntu
/home
/mint
/home 

I purged kernels using remove apt.

---

### Post by deadflowr on 2014-07-13
And what does the boot partition look like, currently.

I'm guessing you can boot a live session,
if so, try to mount the boot partition and run
**ls**
on the partition to see exactly what state it is in.

---

### Post by 3rdalbum on 2014-07-13
> **Wiking said:**
> I was purging some old kernels from my /boot partition and I guess I must have deleted something important because I can't boot into my kubuntu partition.

I downloaded 14.04LTS to boot live into the /home and /  partitions. 

How can I upgrade the old /  and /home partition so that the live CD doesn't overwrite anything just upgrades and updates the old partitions?

thanks

Boot from the Ubuntu CD and choose "Install Ubuntu".

When you are asked if you want to erase the disk, install side-by-side etc, choose "Something Else".

Select the partition that is currently used for /, click the "Change..." button and set the mount point to "/". Click Ok.

Do the same for your existing /boot and /home - set the mountpoints of these to /boot and /home respectively. Do not format the /home or you will lose your data.

Click the Install Now button. You'll be asked a very verbose and difficult-to-understand question about existing mountpoints not being erased; click Continue.

Proceed with the installation as normal. The contents of your /home partition will be retained (note, this works even if /home is on the same partition as /) and your existing software selection will be reinstalled into the new system at the end - it's safe to cancel at that point if you grow tired of waiting.

---

