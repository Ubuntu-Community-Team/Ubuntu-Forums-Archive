---
title: "Backup"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by intense.ego on 2008-08-27
I plan on installing Arch linux alongside ubuntu on my computer, but before I did anything potentially damaging, I wanted to know what I should back up (I assume both my / and my /home partition) and how? A simple terminal command will do. In case you need to know, I will be backing it up to an external HDD.

thank you guys in advance

---

### Post by cariboo on 2008-08-27
I wouldn't bother backing up your / partition, just back up your home partition including the hidden files and you should be ok.

Jim

---

### Post by intense.ego on 2008-08-28
> **cariboo907 said:**
> I wouldn't bother backing up your / partition, just back up your home partition including the hidden files and you should be ok.

Jim

Whoops! Good point, the root is pretty pointless if your home folder is seperated. I could just install Ubuntu again.

Do you know what command I would use to back up /home?

---

### Post by kpkeerthi on 2008-08-28
```

rsync -a /home/<user> /where/my/external/drive/is/mounted/backup

```

---

### Post by intense.ego on 2008-08-28
Cool, thanks

---

### Post by imagenius on 2008-08-28
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

