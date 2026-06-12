---
title: "[SOLVED] re-starting file manager"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by ozzyprv on 2008-07-15
Is there any option of "re-starting" the file manager without having to log-off/restart?

Why? - I just inserted a CD (containing pictures - jpg files) and now I do not get response from the /media/xxxx devices.
I tried Places>Home Folder, etc, and nothing.

Thank you.

---

### Post by shadow-of-sin on 2008-07-15
Type this in the terminal:
```
sudo killall nautilus
```

---

### Post by ozzyprv on 2008-07-15
That was FAST!.
and it worked.

Thanks.

---

