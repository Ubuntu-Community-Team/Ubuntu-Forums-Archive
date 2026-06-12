---
title: "Recover Windows drive with Ubuntu CD"
date: 2011-11-19
forum: New to Ubuntu
---

### Post by cowboybob on 2011-11-19
I recoved all documents fro a Dead drive but I need to find the .pst files from outlook. Does anyone know how to get to them using Ubuntu?

---

### Post by docbop on 2011-11-19
The .pst is file like any other it isn't hidden just have to locate it.   I don't have a Windows box around but if I remember its in the user documents directory and might even be in a Outlook directory.

---

### Post by cowboybob on 2011-11-19
Thats my issue I cant find them, Ive look through every folder.

---

### Post by cowboybob on 2011-11-19
Found it, thanks for the push to keep looking......

---

### Post by WasMeHere on 2011-11-19
> **cowboybob said:**
> Found it, thanks for the push to keep looking......
Glad you found it. But I might as well post a linux tool to find files for use in the future.
The following command line finds all pst files in and below the current directory
```
sudo find . -name \*.pst
```

---

