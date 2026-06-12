---
title: "root"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by nhovan on 2008-05-12
so apparently ... i managed to do something to my SU password. any idea how I can reset it? i can get into the manage groups. i put myself into the root group but i cant login as a SU

any help?

---

### Post by Joeb454 on 2008-05-12
You can't log in as su by default in Ubuntu. If you want to run commands as Root, use the sudo command, i.e. ```
sudo nano /etc/X11/xorg.conf
``` that sort of thing.

If you **really** want to become root, you can run ```
sudo -i
```

---

### Post by Mr A Mouse on 2008-05-12
> **nhovan said:**
> so apparently ... i managed to do something to my SU password. any idea how I can reset it? i can get into the manage groups. i put myself into the root group but i cant login as a SU

any help?

You can reset your root password by going to:

  SYSTEM > Administration > Users and Groups

Unlock Users and Groups with your regular user password, and you can select "root" and change root's password.

This will ONLY work if you already have administrative access.

---

### Post by RedSquirrel on 2008-05-12
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by zvacet on 2008-05-13
@ **nhovan**

Sorry if I didn´t understand you correctly,but do you want to say that you can not run admin tasks because you can not use sudo?If that is the case run in recovery mode and type 

```
adduser username admin
```

---

### Post by Xiong Chiamiov on 2008-05-13
I think that Joeb's interpretation is correct, that you are trying to do
```

su -

```
and it's not accepting the password?

If so, yes, you cannot do that in Ubuntu (it's rather complicated), but you can achieve the same functionality with
```

sudo -s

```
or
```

sudo -i

```

---

