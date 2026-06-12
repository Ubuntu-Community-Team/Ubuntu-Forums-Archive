---
title: "becoming root user without sudo"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by Whizza on 2008-06-13
Hi, I need to become root user and have managed to give root user a password (the documentation says this is all I needed to do). However when I try to use 'su' at the command line and type in my password I am told that my account has expired and I should see the system administrator- problem is, I don't have a system administrator (unless its me). I hopeful that someone can help me become root user so that I can work without 'sudo'

Cheers.

---

### Post by ukripper on 2008-06-13
> **Whizza said:**
> Hi, I need to become root user and have managed to give root user a password (the documentation says this is all I needed to do). However when I try to use 'su' at the command line and type in my password I am told that my account has expired and I should see the system administrator- problem is, I don't have a system administrator (unless its me). I hopeful that someone can help me become root user so that I can work without 'sudo'

Cheers.

use ```
sudo -i
```

---

### Post by aabento on 2008-06-13
I have the same problem. :(

Sudo -i   Doesn't solve it. 
More sugestios?

Thanks
Arnaldo

---

### Post by xeth_delta on 2008-06-13
> **Whizza said:**
> Hi, I need to become root user and have managed to give root user a password (the documentation says this is all I needed to do). However when I try to use 'su' at the command line and type in my password I am told that my account has expired and I should see the system administrator- problem is, I don't have a system administrator (unless its me). I hopeful that someone can help me become root user so that I can work without 'sudo'

Cheers.

Try
```
sudo su
```

And yes, you are the system administrator in your system, when using sudo or the root account.

---

### Post by gr4nf on 2008-06-13
Possibly:
```

sudo su -

```
This may or may not be different from the above.

---

