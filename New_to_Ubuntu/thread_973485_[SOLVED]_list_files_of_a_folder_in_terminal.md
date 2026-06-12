---
title: "[SOLVED] list files of a folder in terminal?"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by niiklas on 2008-11-06
Is there any command to list files inside a folder for example files in /etc/apache2/conf.d/

---

### Post by taurus on 2008-11-06
```
ls -la /etc/apache2/conf.d
```

---

### Post by handydan918 on 2008-11-06
> **niiklas said:**
> Is there any command to list files inside a folder for example files in /etc/apache2/conf.d/

Try ```
/etc/apache2/conf.d/
```


If /etc/apache2/conf.d/ is a directory....


If it isn't (as I suspect) then try 

```
/etc/apache2

```

---

### Post by Gannon8 on 2008-11-06
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
^ Some good terminal basics

And it is a directory :)

---

