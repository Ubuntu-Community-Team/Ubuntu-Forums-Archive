---
title: "Cant save changes to sysctl.conf"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by leotemp on 2008-04-30
the title basically says it all, i need to tweak the sysctl.conf but when i run
sudo gedit /etc/sysctl.conf
I cant save the changes i make and it says "You do not have the permissions necessary to save the file.."

So how would i do this proper?

---

### Post by K.Mandla on 2008-04-30
I'd give it a shot from a different editor, such as nano from the command line.

```
sudo nano -w /etc/sysctl.conf
```

---

