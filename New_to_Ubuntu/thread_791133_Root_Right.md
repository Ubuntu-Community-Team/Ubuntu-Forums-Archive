---
title: "Root Right"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Yappy on 2008-05-11
I don't remember changing any of my password.

Recently, I issue the command su and was prompt with a password. I key in the passpword and a message showed that the password did not match.

So what has gone wrong as I did not change any of the password?

Without the passw how can I go into root?

---

### Post by amingv on 2008-05-11
```
sudo su
```

or better:
```
sudo <command you want to run as root>
```

---

### Post by Sef on 2008-05-11
Moved to absolute beginners.

---

### Post by Sef on 2008-05-11
> I don't remember changing any of my password.

Recently, I issue the command su and was prompt with a password. I key in the passpword and a message showed that the password did not match.

Root is disabled in Ubuntu.  Instead sudo is used.  Read [RootSudo]("https://help.ubuntu.com/community/RootSudo") for more information.

---

