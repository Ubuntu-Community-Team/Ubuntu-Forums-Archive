---
title: "How do I decrypt a folder I made with ecryptfs ?"
date: 2014-04-21
forum: New to Ubuntu
---

### Post by Ploni_Almoni on 2014-04-21
I made a folder yesterday and put all of my sensitive data into it.  I made it with the command

```
mkdir secret
chmod 700 secret
mount -t ecryptfs secret secret
```

Then followed the steps to encrypt it, put my data into the folder and then used:

```
umount secret
```

to unmount it.

Today, I went to mount it again to decrypt it with:

```
mount -t ecryptfs secret secret
```

and it did what I did not expect; it led me through encrypting the folder again.

So how do I decrypt the folder now?  (Now it is doubly encrypted)

---

