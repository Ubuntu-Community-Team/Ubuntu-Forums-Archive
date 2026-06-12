---
title: "$MAIL environment variable empty for unprivileged user"
date: 2015-01-12
forum: New to Ubuntu
---

### Post by smconvey on 2015-01-12
As root, I get the following:
```
# echo $MAIL
/var/mail/root
```
As a nonprivileged user, I get the following:
```
$ echo $MAIL

$
```
In Fedora and OpenSUSE, nonprivileged users get a mailbox in /var/mail/. Is this something that Ubuntu does differently? Can anyone provide a link to official documentation that discusses this?

---

### Post by TheFu on 2015-01-13
So ... I've never had any issue with email on my ubuntu systems. Never noticed the environment variable as missing. Things sorta just work.

Perhaps if you said what you were trying to accomplish, we could help?

Of course, you could always just set the env that you want.  Often there are defaults which are assumed if there isn't any env set.

---

