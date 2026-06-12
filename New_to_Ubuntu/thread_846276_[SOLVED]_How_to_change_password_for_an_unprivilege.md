---
title: "[SOLVED] How to change password for an unprivileged account"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by imjscn on 2008-07-01
I added an account like this:

sudo groupadd myaccount2
sudo useradd --gid sandbox --shell /bin/false myaccount2--home /nonexistent
sudo smbpasswd -a myaccount2

Now I forgot the password. I tried to reset it in the Users and Groups, the new password doesn't work either, what can I do now?

---

### Post by hyper_ch on 2008-07-01
```

sudo passwd USER

```

not sure about the samba password... that has to be changed individually

---

### Post by sisco311 on 2008-07-01
To change the samba password:
```
sudo smbpasswd USERNAME
```

---

### Post by imjscn on 2008-07-01
Thanks!!!

---

### Post by imjscn on 2008-07-01
Hi again,
It seems my samba network setting was incorret, so I deleted the user account which associated with a samba user. Does it mean the samba password automatically deleted or I need to delete something in samba?

---

### Post by sisco311 on 2008-07-02
Theoretically yes.  Try:
```
sudo smbpasswd -x USERNAME
```to make sure USERNAME is deleted from the  local smbpasswd file.

---

### Post by imjscn on 2008-07-02
thanks!!!

---

