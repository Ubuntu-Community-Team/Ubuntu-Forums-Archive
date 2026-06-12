---
title: "Corrupted file in crash folder"
date: 2017-06-23
forum: New to Ubuntu
---

### Post by rdb3 on 2017-06-23
Lubuntu 16.04

I have a file (_lib_systemd_systemd-journal.0.crash) in the crash folder that will not move to trash.

When I try to move it, it tells me that the file was corrupted with errors..... and it remains in crash.

Your suggestions on how to deal with this are appreciated it.  Thanks.

---

### Post by oldos2er on 2017-06-23
Do you want to delete it or save it?

If you want to delete it permanently, try ```
sudo rm /var/crash/_lib_systemd_systemd-journal.0.crash
```

---

### Post by rdb3 on 2017-06-23
> **oldos2er said:**
> Do you want to delete it or save it?

If you want to delete it permanently, try ```
sudo rm /var/crash/_lib_systemd_systemd-journal.0.crash
```

Thanks, it worked!

---

### Post by oldos2er on 2017-06-23
Welcome.

---

