---
title: "[SOLVED] question about moving files with mv command"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by jjblackfox on 2008-07-04
Is it possible to move more than one file at a time? I want to add multiple brushes to gimp and I don't have access to paste them in the folder so I am using sudo mv.

---

### Post by rzrgenesys187 on 2008-07-04
Yep its possible and very easy: for example

```
sudo mv file1 file2 file3 etc /home/user/destination
```

this moves file1, file2, file2, etc to /home/user/destination

---

### Post by finer recliner on 2008-07-04
launch nautilus with root privileges if you like using drag-n-drop

```
gksudo nautilus
```

---

### Post by jjblackfox on 2008-07-04
> **rzrgenesys187 said:**
> Yep its possible and very easy: for example

```
sudo mv file1 file2 file3 etc /home/user/destination
```

this moves file1, file2, file2, etc to /home/user/destination

Thanks, I tried commas and semi colons, but never just spaces.
finer recliner, thanks for the tip. I'm trying to get used to the terminal now, but I will definitely use this later, it seems much faster.

---

### Post by cariboo on 2008-07-04
If the files all have the same extension you can use the wildcard in Ubuntu also:

```
sudo mv *ext /directory
```

Jim

---

### Post by jjblackfox on 2008-07-04
> **cariboo907 said:**
> If the files all have the same extension you can use the wildcard in Ubuntu also:

```
sudo mv *ext /directory
```

Jim

Wow thanks, that was really helpful :)

---

