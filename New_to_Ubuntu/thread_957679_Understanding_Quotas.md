---
title: "Understanding Quotas"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by Mr_H on 2008-10-24
I've figured out how to setup and activate quotas on my Ubuntu server.  I also know how to go in and edit users and groups quota limits, but I have a question regarding how those limits are read.

Lets say I have two groups: Basic group has a quota limit of 500 MB.  Advanced group has a limit of 5GB.
If Bob is a member of Advanced group, Im assuming he gets the 5GB limit, correct?

However, if I go in and edit Bob's own quota to be 1GB, will that be his new limit?  Or does the group override the user?

(Also, a coworker had a question:  Is a Group Quota limit the total of the group, or what each individual in the group has? IE, if Bob has 3 GB and Frank has 2GB, they're at their group limit?)

Much thanks
H

---

### Post by kidders on 2008-10-26
Hi there,

> **Mr_H said:**
> Advanced group has a limit of 5GB.
If Bob is a member of Advanced group, Im assuming he gets the 5GB limit, correct?No, not really. Quotas limit the number and/or total size of the files that can be owned by a particular user/group. Membership of a group with a quota doesn't necessarily affect the amount of data you can store on a filesystem at all.

> **Mr_H said:**
> However, if I go in and edit Bob's own quota to be 1GB, will that be his new limit?  Or does the group override the user?Quotas don't override each other ... they operate independently. For example ...[LIST]
[*]Let's say your filesystem contains 4.999GB of files owned by your Advanced group.
[*]Imagine that Bob is a member of both Advanced and Basic.
[*]Suppose that there are only 5 or 10 kB of files owned by Bob on the filesystem.
[/LIST]If bob tries to save a 3MB MP3 using his Advanced membership, the operation won't be allowed, because that would cause the amount of data owned by Advanced to exceed its quota. Depending on how much space Basic is using, he may well be allowed to save the file as that group though.

Of course, if the amount of data owned by Bob is approaching his 1GB user quota, he may be unable to do either.

Is that any help?

---

### Post by Mr_H on 2008-10-26
Yup, that's a ton of help.  Thanks for clearing that up for me:)

---

