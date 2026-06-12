---
title: "Auto mounting an external drive"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by Azalar on 2008-05-24
I have an external drive that I use to store multimedia and I want to setup the fstab file so that it will use a specific mount point when i switch it on.
I have the correct UUID but I know the other parts of it are wrong.
Here is what I have so far..

UUID=e85388f0-aa1d-43f7-bf69-5bce366759c2 /media/Multimedia ext3 relatime,errors=remount-ro 0 2

I'm guessing the part that is wrong is relatime,errors=remount-ro

Its not letting me mount it as a user with this setting but then it was just copied from one of the others in the same fstab file.
Also because its setup like this the OS wont boot at all unless I have the external drive connect when I reboot as it can't find the device with that UUID.

So basically what I want to do is have the fstab line setup so that there isn't any requirements for the drive to be there at bootup and when I switch on the external drive for it to automount the drive at /media/Multimedia and allow the user to read/write to it.

Thanks in advance for any help anyone can give me on fixing this.

---

### Post by strider1551 on 2008-05-24
> Its not letting me mount it as a user

That can be easily fixed, just use the "users" option.

```
UUID=e85388f0-aa1d-43f7-bf69-5bce366759c2 /media/Multimedia ext3 users,relatime 0 2
```

As for automounting the device when you turn it on, I don't believe that can be accomplished through /etc/fstab

---

### Post by Azalar on 2008-05-25
When i first set this up before I added the line is the fstab file Linux would auto mount the drive anyway when it was switched on.
But it would just create a new mount point in /media and assign its own name to it, I think based on what the disk label is set to.
I just want to be able to have control over that process and set my own mount point and thought this was possible if setup via the fstab file.
Anyone know if this is possible via fstab or is there another way to do this?

---

