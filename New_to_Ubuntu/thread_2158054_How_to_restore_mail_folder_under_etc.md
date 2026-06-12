---
title: "How to restore mail folder under /etc?"
date: 2013-06-27
forum: New to Ubuntu
---

### Post by Houmie on 2013-06-27
upon installation...

```

sudo apt-get install sendmail
```

it created a folder called /etc/mail

due various configuration problems, I have uninstalled it
```

sudo apt-get remove --purge sendmail
```

when I now reinstall it, the folder is not there anymore and neither can I run the

```
sudo sendmailconfig
```

because of the missing folder.

Any suggestions?

---

### Post by SeijiSensei on 2013-06-27
Try running "dpkg -S sendmail" which will list all the files installed on your system from the sendmail package.  What do you see?

---

### Post by Houmie on 2013-06-28
Hey thanks,

I was able to restore it by 

> sudo apt-get install sendmail-base

---

