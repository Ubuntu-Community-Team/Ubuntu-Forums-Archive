---
title: "Cannot share a FUSE mountpoint"
date: 2012-01-16
forum: Programming Talk
---

### Post by Asmodai on 2012-01-16
Hey,

I have a FUSE filesystem and now I'd like to share the mount point on the network.
However, when I add a share using the Nautilus dialog, I get no error messages, but the the share never shows up on the network.

I'm figuring I need to implement some additional operations for it to work, but which ones? At the moment only getattr, readdir, open, release and read are implemented.
Browsing and accessing the file system via Nautilus etc. on my local machine works just fine.

Any help would be appreciated.

Edit: implemented access() too. The logs show that the entire directory structure is read and stat() performed on all files after adding the share - still, it never shows up in the network.
Edit2: added chmod() and chown(), but they're never called.
Edit3: added statfs(), but only setting the max file name length to 60000 and everything else to 0. Didn't change anything, though.
When I manually add the share to /etc/samba/smb.conf (with browseable = yes, read only=yes and guest ok = yes), it shows up in the share list, but I still can't access it.
For example, using smbclient, I get NT_STATUS_BAD_NETWORK_NAME. My directories have umask 0755 and my files 0444. That should be okay, right?
Edit4: the problem persists even when I remove all directories and files except the root directory. What on earth is going on?

---

### Post by Asmodai on 2012-01-16
Apparently you need to start the program as root with the option -o allow_other and add user_allow_other in /etc/fuse.conf for this to work.
And to think I've been hunting non-existant bugs for hours... well, I'm glad it works now.

---

### Post by Habitual on 2012-01-17
+1 for finding your own solution.

---

