---
title: "problem creating quota in ubuntu 12.04"
date: 2013-08-18
forum: New to Ubuntu
---

### Post by darkchest on 2013-08-18
I was trying to make quota limits for an admin user using the tool quota, quotacheck and edquota. I edited the /etc/fstab. Initially when i did the quotacheck it worked.

Now when i do ```
quotacheck -mavug
``` i get the following output:
```
quotacheck: Quota file //aquota.user has corrupted headers. You have to specify quota format on command line.
quotacheck: Cannot guess format from filename on /dev/disk/by-uuid/ed3dfb36-b36c-4390-b049-743d5be17f80. Please specify format on commandline.
quotacheck: Cannot find filesystem to check or filesystem not mounted with quota option.
```

also when i do ```
quotaon -avug
``` i get the following output:
```
quotacheck: Quota file //aquota.user has corrupted headers. You have to specify quota format on command line.
quotacheck: Cannot guess format from filename on /dev/disk/by-uuid/ed3dfb36-b36c-4390-b049-743d5be17f80. Please specify format on commandline.
quotacheck: Cannot find filesystem to check or filesystem not mounted with quota option.
```.

I have searched how to fix this problem and none has worked. Any help?

---

