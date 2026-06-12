---
title: "crontab -e? -r? how come it doesn't remove file?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by gotquestions on 2008-05-21
Hi,
I can see that there is a crontab file located here:

/etc/crontab

If I am on the prompt and I either do crontab -e or -r, why doesn't it update the changes to: /etc/crontab ???

is it located in another directory? if so how can i find it?

---

### Post by y-lee on 2008-05-21
Probably because you don't have permission.

Try sudo crontab -e instead.

---

### Post by mali2297 on 2008-05-21
I'm not certain, but my guess is that /etc/crontab only contains the jobs for root. To edit that file, try
```

sudo crontab -e

```

If you run
```

crontab -e

```
then you will edit the jobs for your ordinary user. See if there is some related file in your home directory with
```

ls -A ~

```
If you still can't find it, check
```

locate crontab

```

---

