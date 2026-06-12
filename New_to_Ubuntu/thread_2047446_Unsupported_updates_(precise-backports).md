---
title: "Unsupported updates (precise-backports)"
date: 2012-08-24
forum: New to Ubuntu
---

### Post by rbowen1 on 2012-08-24
I just installed 12.04 LTS after using 11.04 for the past couple of years but still feel like a Linux newbie.   Looks good so far :).    After running update manager, I checked the settings for Update Manager and noticed that  under the Update tab, Unsupported updates (precise-backports) is checked.     Is Unsupported updates (precise-backports) checked by default?     Should I remove the check  from "Unsupported updates (precise-backports)"?

All advise is greatly appreciated!

---

### Post by Easy Limits on 2012-08-24
No harm in leaving it check marked.  I hardly ever see anything come from the backport portion of the update.

---

### Post by 2F4U on 2012-08-25
It is considered a bug that this repository is enabled by default:

[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/956405](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/956405)

So, if you are conservative, you are probably better off to disable the repository.

---

### Post by 3rdalbum on 2012-08-25
> **2F4U said:**
> It is considered a bug that this repository is enabled by default:

[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/956405](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/956405)

So, if you are conservative, you are probably better off to disable the repository.

However, it's almost certain that you won't have any ill effects from leaving that repository enabled. You might get one or two newer versions of programs eventually from it, but that's about it.

---

### Post by rbowen1 on 2012-08-26
Thanks for the replies.  I am marking this thread as solved.

---

