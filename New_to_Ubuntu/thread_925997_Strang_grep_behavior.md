---
title: "Strang grep behavior"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by bprof on 2008-09-21
I ran this command on slackware

#df | grep /dev/sda

and got something like this
/dev/sda 1234544 12433 1312111 %1 /var

But on Ubuntu I get only this
/dev/sda

How I can get the full line instead of just /dev/sda?

Thank you,

---

### Post by bab1 on 2008-09-21
What does the df return without the pipe through grep?

---

### Post by t0p on 2008-09-21
```
t0p@ubunty:~$ df | grep /dev/sda1
/dev/sda1             18655308  13972612   3742496  79% /

```

---

