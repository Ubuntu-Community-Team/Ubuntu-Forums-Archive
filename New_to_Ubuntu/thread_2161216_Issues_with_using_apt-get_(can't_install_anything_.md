---
title: "Issues with using apt-get (can't install anything with it)"
date: 2013-07-09
forum: New to Ubuntu
---

### Post by impinball on 2013-07-09
I have looked all over this forum for a solution and none of them ever worked. Keep in mind that although I am fairly familiar with computers, my expertise is with Windows, not Linux.

Now to the issue: I am consistently running into the same issue over and over with the shell:
```
<username>@<computer>:~$ apt-get install git
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```

I've tried many different things that I saw on the forums, none of which helped me on this. Any ideas?

---

### Post by eriktheblu on 2013-07-09
Looks like you need to invoke root permissions.
instead of ```
apt-get install git
``` try ```
sudo apt-get install git
```

---

### Post by impinball on 2013-07-09
That worked. Thanks!

---

