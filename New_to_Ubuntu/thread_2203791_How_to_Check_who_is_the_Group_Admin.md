---
title: "How to Check who is the Group Admin"
date: 2014-02-05
forum: New to Ubuntu
---

### Post by Mohan1289 on 2014-02-05
Hey Guys.. 

How can i check who is the Group Adminstrator of a particular Group in Linux Server??

Thanks 

Krishna

---

### Post by Dave_L on 2014-02-05
Are you asking how to determine which users are in the group named "admin"?

---

### Post by Mohan1289 on 2014-02-15
> **Dave_L said:**
> Are you asking how to determine which users are in the group named "admin"?


Nope i want to check who is the Group Administrator of a Particular Group...

Is  that possible???

Thanks

---

### Post by Iowan on 2014-02-15
Group Administrator? I'm also a bit confused. **root**?
As far as I know, there is no separate administrator for each group.

---

### Post by Dave_L on 2014-02-15
I wasn't previously aware of this feature.

```
sudo cat /etc/gshadow
```

The third field of each line is the list of group administrators.

References:
[http://manpages.ubuntu.com/manpages/precise/en/man5/gshadow.5.html](http://manpages.ubuntu.com/manpages/precise/en/man5/gshadow.5.html)
[http://manpages.ubuntu.com/manpages/precise/en/man1/gpasswd.1.html](http://manpages.ubuntu.com/manpages/precise/en/man1/gpasswd.1.html)

---

### Post by Iowan on 2014-02-15
I learned something new!

---

