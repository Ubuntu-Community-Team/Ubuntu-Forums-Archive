---
title: "How to get locks off of folders?"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by WBL on 2008-04-28
I just transferred a bunch of folders containing .mp3 music files from a burned CD to my "Music" folder.  All of these folders have lock icons attached to them!  :confused:

Does anyone know how to remove these lock icons on my folders?

Thanks in advance.

-WBL

---

### Post by Tatty on 2008-04-28
It sounds like a permissions problem

```
sudo chown *username*:*groupname* -R */path/to/folder*
```

should fix it.

Makes sure you put in the correct path though, you dont want to be chowning the wrong thing!

---

