---
title: "Mailx"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by Frank_F on 2008-07-15
Hello

Does anyone know how I send out an email to the outside world using mailx ?

Thanks

---

### Post by brian_p on 2008-07-15
> **Frank_F said:**
> Hello

Does anyone know how I send out an email to the outside world using mailx ?

mailx uses exim4 to send the mail so exim4 has to set up for non-local delivery.

```
sudo dpkg-reconfigure exim4-config
```

---

