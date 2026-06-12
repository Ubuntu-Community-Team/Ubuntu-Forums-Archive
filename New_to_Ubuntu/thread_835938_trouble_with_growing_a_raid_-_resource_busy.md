---
title: "trouble with growing a raid - resource busy"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by rogueluke on 2008-06-21
I am trying to add a harddrive to my raid device.

I got a new harddrive that is the same size as the other drives in my raid and i am trying to increase the size.  When i went to partition and format the drive gparted would not do it because it said the disk was in use.  I could not understand it because i was not mounting the drive.  I eventually got it partitioned and formated using the live cd.

Now i go to do the mdadm --add and i get

mdadm: Cannot open /dev/sdd7: Device or resource busy


this doesn't make sense, i have made sure that sdd is not in the fstab but thats about all i know to look.

I have checked online but no one seems to have the same problem as me, most of them are trying to change the hardrive sizes and are having issues with that but im just trying to add 1 hd which shouldn't be a problem.


is it possible to do this with the livecd and just avoid the issue altogether,  if so how do i get the mdadm info back onto the file system?


thanks for any help.

---

### Post by rogueluke on 2008-06-21
maybe somemore info.  I just noticed that my cd drive was going crazy.  theres no disk in it but it keeps flashing the light and sounding like its trying to read.  i checked out /var/log and the logs are going crazy.  the kerel log keeps saying that its failing with something like a device detect.  sorry for not having the exact messages.  and my udevd process is going crazy.

i know that my cd rom drive was not doing that before i added to new hd in.  im going to yank the drive out tomorrow and see if that stops the cdrom issue.  again any help would be appreciated but it seems like the kernel or someone is just pounding on the drives trying to mount it or something.


thanks.

---

### Post by rogueluke on 2008-06-21
K fixed it, next time dont install evms.

---

