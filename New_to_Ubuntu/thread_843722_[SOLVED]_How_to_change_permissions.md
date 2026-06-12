---
title: "[SOLVED] How to change permissions?"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by bhadotia on 2008-06-28
I have just now reinstalled ubuntu (3 hrs ago) coz I had dne quite a bit of experimenting with the last one and could not make a clean escape :). I  made my self a seperate partition for my data in this install and mounted it on /data. The problem is /data now belongs to root , so I cannot read or write from that. Can some one please tell me how to change the owner (or atleast the permissions) of /data.
Many thanx in advance.
PS: I have made this same post in another thread . But because there were no replies , I made this seperate thresd for this question.

---

### Post by nick_h on 2008-06-28
Is it an ext3 filesystem?

You can change the owner and group using the *chown* command:
```
sudo chown username:username /data
```

Then you can change the permissions either by the *chmod* command or from within nautilus. (Right-click on the folder -> properties then select the permissions tab).

For the manual pages type:
```
man chown
man chmod
```

---

### Post by bhadotia on 2008-06-28
K........ thanks .

---

