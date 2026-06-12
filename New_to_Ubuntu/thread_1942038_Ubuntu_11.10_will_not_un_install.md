---
title: "Ubuntu 11.10 will not un install"
date: 2012-03-16
forum: New to Ubuntu
---

### Post by kn4hh on 2012-03-16
First many thanks for the great assistance this forum has provided me.  I must be overlooking something basic with this problem.
I have a dual boot XP pc with Ubuntu 11.10 installed.  I wanted to uninstall Ubuntu and run it on another dedicated pc.  I used GParted and deleted all of the Linux partitions and resized the NTFS partition. Then I booted the pc with the XP installation CD and used the Repair console to run fixboot and fixmbr.  I then rebooted and The options still appeared for either XP or Ubuntu.  Even stranger,in addition to a good XP boot, I could also still boot up in Ubuntu but with very limited response.  I repeated the procedure detailed above and the result was the same.

I also used Disk Manager under XP and confirmed no other partitions exist than the NTFS partition which occupies the entire Hard drive.

Would really appreciate some guidance with this one.

Thanks,
Bob Watson

---

### Post by Basher101 on 2012-03-16
soo what you're telling me is...you wiped the Ubuntu partition, restored the MBR, but you can still boot ubuntu? how is that even possible? I can't think of aynthing as i am baffled at the moment..

---

### Post by kn4hh on 2012-03-16
As odd as it sounds, yes all but the NTFS partition is gone.  The grub boot loader still loads and Ubuntu 11.10 still appears to load.  Is it possible to create a linux image in NTFS?

---

