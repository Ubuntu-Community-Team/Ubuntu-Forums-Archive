---
title: "remove default bookmarks"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by rkakkar on 2008-11-06
how do i permanently remove the documents, music, pictures and videos bookmarks? they seem to re-appear on every login.

---

### Post by stoogiebuncho on 2008-11-07
Are you talking about the folders that appear in the side bar of Nautilus (the file manager) or something else?

---

### Post by rkakkar on 2008-11-08
> **stoogiebuncho said:**
> Are you talking about the folders that appear in the side bar of Nautilus (the file manager) or something else?

yup!

---

### Post by stoogiebuncho on 2008-11-08
You could try editing the user-dirs.dirs file.

```
gedit ~/.config/user-dirs.dirs

```

You'll probably want to make a backup of the file first, just in case you change something that you didn't mean to change.

I haven't tried this myself, just seems like a good place to start.

---

