---
title: "changed fstab but nothing seems to happen"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by holdie on 2008-11-02
I've been trying to get my /home folder on a new partition for quite some time now...I've done everything following psychocat's guide, and it works fine if I mount my home partition to the /home folder before booting

However, if I just boot as normal then the computer doesn't see that there is anything inside the /home folder and messes up

I've edited fstab, adding a line at the end that should mount my other partition to home, but it would appear that the computer isn't doing this

any ideas?

---

### Post by b0b138 on 2008-11-02
Please post your fstab file

---

### Post by aramadia on 2008-11-02
What do you mean by mounting a partition before booting?  Before rebooting it was working?  Yeah post fstab.  You probably need the auto flag which tells ubuntu to mount it automatically.

---

