---
title: "Usernames, groups and privilidges problems"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by luvinit on 2008-07-17
Hi,
Someone who knows jack about Linux was going to be accessing my computer using my username, so I though it would be a good idea to remove admin privileges from my account so that they couldn't cause any damage. Anyway, I did that, but now I can't restore admin back to my username. The option doesn't become available in "properties". Currently only root has admin capability, but you are not able to login as root and sudo cannot be used on my username since I removed admin ability from it. How the hell do I fix that?
Thanks.

---

### Post by unutbu on 2008-07-17
Reboot, press ESC to get to the GRUB menu. Boot into Recovery Mode. This drops you to a root shell.

Type:

```
gpasswd -a USERNAME admin
```

changing USERNAME to your real username.

Type
```

init 2
```
to resume a regular boot.

---

### Post by luvinit on 2008-07-17
Hey, you make it look so simple. Thanks. :)

---

