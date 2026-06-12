---
title: "[bash] Checking for a directory in root"
date: 2010-04-30
forum: Programming Talk
---

### Post by AntumDeluge on 2010-04-30
I'm trying to check if a directory exists under root, but if I don't have root permissions, it returns as false.  

```
if [ -d "/root/Desktop" ]; then echo "hello world"; fi

```How do I check for a root directory if I don't have permission?  Or, how do I use my sudoer permissions to check for a directory?

---

### Post by tookyourtime on 2010-04-30
What happens if just just run the script with
```

sudo ./testscript
```
?

---

### Post by AntumDeluge on 2010-04-30
You're totally right.  For some reason I was thinking that I wanted to run this script without sudo, but now that I think it through, that is what I want to do.  Thanks.

---

