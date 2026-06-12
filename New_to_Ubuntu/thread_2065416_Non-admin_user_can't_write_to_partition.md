---
title: "Non-admin user can't write to partition"
date: 2012-10-01
forum: New to Ubuntu
---

### Post by heebiejeebies on 2012-10-01
Hi all,

I'm running ubuntu through wubi and I have the main drive partitioned into 2 to provide a common storage area between ubuntu and Windows.  I was able to access this without any difficulties when logging in as admin.  Only problem is, I need some users to not have admin access - but these users are asked to authenticate with an admin password before they can see the drive.  I've tried granting them permission in the permissions window but it does nothing.  The settings immediately change back to restrictive.  I'm hoping there's a simple line or two I can add to a startup script that will give them read/write access to the partiton.  Can anyone provide me with such a line or suggest an alternative solution?

Thanks! :-)

---

### Post by critin on 2012-10-01
> I'm running ubuntu through wubi and I have the main drive partitioned  into 2 to provide a common storage area between ubuntu and Windows

You know wubi is installed inside windows, its partition is a section of the windows partition.  How did you separate the two like this?

As for other users using the storage area, sharing should allow it from ubuntu.  Can they see the partition from their file manager or how do they access it?  Is everything is allowed to share?
If it's windows that needs the permission, you may need to go into windows and create a lan, sharable with all, no password req.  A workgroup lan.

---

### Post by heebiejeebies on 2012-10-02
Yep, ubuntu and windows are on the same partition as usual.  But the disk is partitioned into 2 which gives me a common storage area between the two.  I guess I can try with sharing, although the non-admin users can already see the drive in naultilus.  Just that when they try to access it, it asks for an admin password.

---

### Post by sandyd on 2012-10-02
> **heebiejeebies said:**
> Yep, ubuntu and windows are on the same partition as usual.  But the disk is partitioned into 2 which gives me a common storage area between the two.  I guess I can try with sharing, although the non-admin users can already see the drive in naultilus.  Just that when they try to access it, it asks for an admin password.

that sounds like you have the partition in /etc/fstab

post the output of
```

cat /etc/fstab/
```

---

