---
title: "[SOLVED] missing all personal settings"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by mykyi on 2008-08-15
Hello all

I was trying to move my home to a new partition and some how i messed up permissions.  I couldn't log in to ubuntu at all, it said i have to own desktop to log in. I found a thread and did a 

```

chown -R mike:mike /home/mike

```

I'm back in ubuntu now however my awn dock did not start and my background defaulted to ubuntu standard.  I go to home and non of my things are in there. When I start Picasa I can see my pics in there for a millisecond and then it disappears.  I guess I've wiped my home or something.  Any help would be appreciated 

Thanks

mykyi

---

### Post by Pro-reason on 2008-08-16
If you don't have permission to edit some of the files in there, the chown command won't change those permissions.  You might need to do "sudo" in front of it to force that.  You might also need to run "chmod" on the files.

---

### Post by cdtech on 2008-08-16
When moving your home partition you must also change your settings within the /etc/fstab file:
```
# Entry for /dev/sda6 :
**UUID=aed3efe3-53d1-4b88-9c36-c87678436f45** /home ext3 defaults 0 1
```
By changing the UUID (block id) to the new partition's block id.

You can find the UUID by issuing the command (in a terminal):
```
blkid
```

Hope this helps.....

---

### Post by Pro-reason on 2008-08-16
> **cdtech said:**
> When moving your home partition you must also change your settings within the /etc/fstab file:
```
# Entry for /dev/sda6 :
**UUID=aed3efe3-53d1-4b88-9c36-c87678436f45** /home ext3 defaults 0 1
```
By changing the UUID (block id) to the new partition's block id.

You can find the UUID by issuing the command (in a terminal):
```
blkid
```

Hope this helps.....
If the drive has a volume label, then it's an even better way of referring to it than a UUID.

---

### Post by mykyi on 2008-08-16
Thanks guys , I got it figure out, My new partition was indeed mounted @ home  but I never copied the files over from the old home folder that i created. I browsed to old home, did a ctrl-H Copied and pasted everything to Home and boom everything's back.

---

