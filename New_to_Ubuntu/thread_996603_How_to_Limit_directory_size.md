---
title: "How to Limit directory size"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by Guruprasad on 2008-11-29
Hi

I want to create 25 directories and want to limit the maximum size of the directory to 1GB only.

All these directories will belong to each staff of office. I do not want them to use more than 1GB of space.

---

### Post by nhasian on 2008-11-29
To manage disk quotas, you must have the *quota* and *quotatool* packages installed on your system. Quota management with Ubuntu is not enabled by default.

The root of the partition with quotas enabled will have the files quota.user or quota.group in them (or both files, if both types of quotas are enabled), and the files will contain the actual quotas. The permissions of these files should be 600 so that users cannot read or write to them. (Otherwise, users would change them to allow ample space for their music files and Internet art collections.) To initialize disk quotas, the partitions must be remounted. This is easily accomplished with the following:

```
mount -o ro,remount partition_to_be_remounted mount_point
```

The underlying console tools (complete with man pages) are:

[LIST]
[*]quotaon, quotaoff—Toggles quotas on a partition
[*]repquota—A summary status report on users and groups
[*]quotacheck—Updates the status of quotas (compares new and old tables of disk usage); it is run after fsck
[*]edquota—A basic quota management command
[/LIST]

this link may help too:

[http://bytes.com/answers/unix/842583-user-quotas](http://bytes.com/answers/unix/842583-user-quotas)

---

