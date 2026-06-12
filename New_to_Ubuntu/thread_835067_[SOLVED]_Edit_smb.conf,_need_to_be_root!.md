---
title: "[SOLVED] Edit smb.conf, need to be root!"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by batfastad on 2008-06-20
Hi guys
Just been trying to edit my smb.conf but I need to be root.
And I've found out that root in Ubuntu is disabled.

I've tried various shell editors and I totally managed to mangle the smb.conf file with the vim using the sudo command.

Is there a way I can just edit it with mousepad or something in xfce?

Thanks, B

---

### Post by iaculallad on 2008-06-20
Sure do: Same thing with sudo vim as for sudo mousepad.

```
sudo mousepad /etc/samba/smb.conf
```

---

### Post by batfastad on 2008-06-20
Ah ok, that's pretty obvious.
Thanks for the tip!

---

