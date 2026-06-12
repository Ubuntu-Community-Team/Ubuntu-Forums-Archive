---
title: "Problems Scripting Append and Replace as Sudo"
date: 2008-05-24
forum: Programming Talk
---

### Post by jmtritch on 2008-05-24
I am writing some scripts that require replacing (>) and appending (>>) within folders and files owned by root.  Here is a sample command:

```
sudo echo "append this" >> /etc/samba/smb.conf
```

This returns "**bash: /etc/samba/smb.conf: Permission denied**."  I presently work around it by copying the file to a location where I have proper permissions, appending to that file, and then copying that file back to the its destination as the super user.

Is there a more efficient way?

---

### Post by geirha on 2008-05-24
You can use tee like this:
```
echo "append this" | sudo tee -a /etc/samba/smb.conf
```
or you can put the whole thing in a shell with super user privileges:
```
sudo bash -c 'echo "append this" >> /etc/samba/smb.conf'
```

---

### Post by jmtritch on 2008-05-25
tee worked like a charm.  Thanks!

---

