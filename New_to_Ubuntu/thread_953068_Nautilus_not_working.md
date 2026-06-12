---
title: "Nautilus not working"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by Lorelei- on 2008-10-19
It seems that nautilus doesn't work on my Dell pre-installed machine, but I have no idea why it wouldn't as I'm the only user. When I try to run it I get this:

> seahorse nautilus module initialized
Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:1417): WARNING **: Unable to add monitor: Operation not supported
seahorse nautilus module shutdown

How do I resolve this so that it will run properly?

---

### Post by fslezak on 2008-10-19
Are you the only user? Is your monitor set up? Are you in the Admin group?

---

### Post by Bucky Ball on 2008-10-19
It looks like samba is maybe not installed, but odd as it should not need to be to run Nautilus. There is a workaround in the Samba Shares section on this page:

[http://ubuntuforums.org/showthread.php?t=773851](http://ubuntuforums.org/showthread.php?t=773851)

---

