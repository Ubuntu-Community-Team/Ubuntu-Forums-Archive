---
title: "how to update server through SSH"
date: 2013-12-27
forum: New to Ubuntu
---

### Post by enio-san on 2013-12-27
Hi everyone.
I just purchased a cloud server account, which includes Ubuntu 12.04. When logging in using SSH, it reports that there are some 'security updates available'... and also 'you have a new email'.

So, I ran the command

[B]$ sudo apt-get update
[/B]
(just like my when I update my ubuntu laptop). Seems to end successfully. But, if I exit SSH, and re-log in, the same 'security updates are available' thing comes up...  like it didnt update anything.
Should I re-boot?... and if I re-boot, should it return all to normal?

Please help !
PS, what is that 'NEW MAIL' note there ?

---

### Post by ptn107 on 2013-12-27
You mean you did a```

sudo apt-get upgrade
```
right?
```
sudo apt-get update
```
just checks for updates.  The *upgrade* command installs them.

---

### Post by plurga on 2013-12-28
hi 

can u post the output of  sudo apt-get update ??

thanks.

---

### Post by CharlesA on 2013-12-28
> **enio-san said:**
> Hi everyone.
I just purchased a cloud server account, which includes Ubuntu 12.04. When logging in using SSH, it reports that there are some 'security updates available'... and also 'you have a new email'.

So, I ran the command

[B]$ sudo apt-get update
[/B]
(just like my when I update my ubuntu laptop). Seems to end successfully. But, if I exit SSH, and re-log in, the same 'security updates are available' thing comes up...  like it didnt update anything.
Should I re-boot?... and if I re-boot, should it return all to normal?

Please help !
PS, what is that 'NEW MAIL' note there ?

It looks like  ptn107 already covered the bit about upgrading packages.

As far as the mail notification goes, just type "mail" and it will show you any unread messages you have waiting. I have seen them show up from cron before.

> **plurga said:**
> hi 

can u post the output of  sudo apt-get update ??

thanks.

Doing apt-get update only refreshes the index of the repo. You need to do apt-get upgrade or apt-get dist-upgrade to upgrade the installed packages.

---

### Post by enio-san on 2013-12-28
THANK YOU ALL!!!
that should do the job.

---

