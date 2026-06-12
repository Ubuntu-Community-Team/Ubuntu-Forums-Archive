---
title: "solution to Fstab issue with securing /tmp and /var/tmp"
date: 2015-08-18
forum: New to Ubuntu
---

### Post by Pokey_blue32 on 2015-08-18
Since the thread is closed I will have to implement this another way. NOBODY and I MEAN NOBODY is posted yet how to properly do this.
/tmp in tmpfs is fine
/dev/shm in tmpfs and limited size is GOOD.
/var/tmp mounted with similar permissions as /tmp is EVEN BETTER. Problem is:

everyone is leaving /var/tmp in RAM in tmpfs instead of leaving it on the /(root) filesystem, where it belongs. /var/tmp IS SUPPOSED to stay beyond a reboot.
/tmp is not.

BIND mounting /tmp to /var/tmp is showing your intelligence and embarrassing us all. Yall are making /var/tmp to NOT survive a reboot. THIS IS WRONG.

So far I have the following edits on /etc/fstab:

tmpfs /tmp tmpfs defaults,noatime,nosuid,nodev,noexec,mode=1700 0 0
tmpfs /dev/shm tmpfs defaults,noatime,nosuid,nodev,noexec,mode=1700,size=4G 0 0

#/var/tmp /var/tmp none rw,relatime,noexec,nosuid,nodev,mode=1700,size=5G,bind 0 0


The last line being either a deal breaker(Refusing to work, breaking boot) or failing to mount properly.
It is QUITE POSSIBLE to mount /var/tmp there (on itself) but bind mounts dont need a fs type specified. Im still working on a final solution to this one. (/var/tmp) Using / as the first argument puts it on /dev/sda1 but without all of the permission goberty-gook you need set.

The first step in this was to octi-fy the permissions. Despite what others are using I find this setup MOST SECURE. Nobody else should be able to edit your IPC data or temp files. ROOT ALWAYS HAS ACCESS.You could set the group permission in case root got hacked but if root does get hacked, you have MORE SERIOUS issues than people here can help you with.

---

### Post by QIII on 2015-08-19
Which thread?  Your answer is a bit ambiguous without a question for reference.

---

