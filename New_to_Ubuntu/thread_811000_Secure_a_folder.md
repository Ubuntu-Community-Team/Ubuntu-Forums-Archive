---
title: "Secure a folder"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Sub101 on 2008-05-28
I have a folder on my desktop which i would like to secure the folder and its contents. How can i go about doing this? Thanks

---

### Post by Monicker on 2008-05-28
Is this a folder which you specifically created?

You could always use chmod to make sure that only the owner, yourself, has access to the directory.
```

chmod 700 /home/username/privatefolder
```

---

### Post by dje on 2008-05-28
You could right click on it and select encrypt (in 8.04)

hope that helps,
dje

---

### Post by Sub101 on 2008-05-29
> **Monicker said:**
> Is this a folder which you specifically created?

You could always use chmod to make sure that only the owner, yourself, has access to the directory.
```

chmod 700 /home/username/privatefolder
```

Thanks worked perfectly. Set as 7000 rather than 700 but still successful.

---

