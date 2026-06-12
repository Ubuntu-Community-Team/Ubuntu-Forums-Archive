---
title: "Cannot add new user and cannot login!"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by kiddy12 on 2008-07-20
OK, this is annoying:

useradd -d /home/john2 -m -p mypassword john2 -s /bin/bash

(cannot login)

WHY?

I put my homedir, i put even a shell...why this is happening?

---

### Post by cdtech on 2008-07-20
Try using "sudo useradd -d /home/john2 -m -p mypassword john2 -s /bin/bash"

---

### Post by kiddy12 on 2008-07-20
I was already root by sudo su, that's not the problem.

---

### Post by ibutho on 2008-07-20
Is the user successfully created? You can check this by doing
```
grep -i john2 /etc/passwd
```
If the user is successfully created, then maybe its a problem with the password (I usually create the password separately using the passwd command), so try resetting that.

---

### Post by kiddy12 on 2008-07-20
> **ibutho said:**
> Is the user successfully created? You can check this by doing
```
grep -i john2 /etc/passwd
```
If the user is successfully created, then maybe its a problem with the password (I usually create the password separately using the passwd command), so try resetting that.

Yes, it's successfully created.
> 
john2:x:1003:1003::/home/john2:/bin/bash

---

### Post by ibutho on 2008-07-20
So, have you tried resetting the password by running
```
sudo passwd john2
```

---

