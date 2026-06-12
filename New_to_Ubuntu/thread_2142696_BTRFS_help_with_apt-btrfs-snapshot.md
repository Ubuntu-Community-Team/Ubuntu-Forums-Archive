---
title: "BTRFS help with apt-btrfs-snapshot"
date: 2013-05-06
forum: New to Ubuntu
---

### Post by Kissell on 2013-05-06
I installed apt-btrfs-snapshot

Then everytime I added or removed something with aptitude it created a new snapshot...  so I had hundreds of snapshots.

I wrote deleted all the snapshots, cause everything was fine...  and I did not delete the root "@" snapshot.

But after doing that, my disk volume shows all the space is still in use, however all my files are gone!!!!

Is there any way to get access to my files again without restoring everything from a backup?

---

### Post by Kissell on 2013-05-06
I rebooted and the files are back!  woohoo!  

The good old reboot fixes everything!

---

### Post by Kissell on 2013-05-06
Huh...  they files were there after the reboot...  I did nothing...  after checking back a few minutes later they're all gone again!!!

Yet "df -h" still shows the volume is using the space for the files.

---

### Post by matt_symes on 2013-05-06
Hi

You've got a love the old reboot trick :)

I'll mark this thread as [SOLVED] for you.

Kind regards

---

### Post by Kissell on 2013-05-06
Thanks, I don't see how to mark threads as solved with this new interface....

actually though it wasn't solved after my last comment...  

however, it sorta is now....  I did a "btrfs filesystem balance /mnt/drivepath" and the files seem to be accessible permanently now...  although the CPU is really being torn up by kworker, btrfs and mdadm processes now.  I read that might take a full day per terabyte, so I guess I'll check on it in a few weeks and see if everything is still okay.

---

