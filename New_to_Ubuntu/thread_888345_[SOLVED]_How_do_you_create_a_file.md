---
title: "[SOLVED] How do you create a file?"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by harryliddic on 2008-08-13
How do you create a file in a directory? I have to have a file VIDEO__TS.ifo
in directory /home/harry/Videos/VIDEO_TS. Simple question but my books and my memory fail me.

---

### Post by iaculallad on 2008-08-13
> **harryliddic said:**
> How do you create a file in a directory? I have to have a file VIDEO__TS.ifo
in directory /home/harry/Videos/VIDEO_TS. Simple question but my books and my memory fail me.

On your terminal:

```
gedit /home/harry/Videos/VIDEO_TS/VIDEO__TS.ifo
```

or

```
gedit ~/Videos/VIDEO_TS/VIDEO__TS.ifo
```

---

### Post by prshah on 2008-08-13
> **harryliddic said:**
> How do you create a file in a directory? I have to have a file VIDEO__TS.ifo
in directory /home/harry/Videos/VIDEO_TS. Simple question but my books and my memory fail me.

If you want to create a blank file, you can also use```
touch ~/Videos/VIDEO_TS/VIDEO_TS.ifo
```; if the file exists, nothing will be done (just timestamp updated), but if it doesn't exist, a blank file will be created (with current timestamp).

---

