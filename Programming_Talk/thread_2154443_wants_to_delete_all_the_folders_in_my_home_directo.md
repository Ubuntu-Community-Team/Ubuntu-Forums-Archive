---
title: "wants to delete all the folders in my home directory which ends with &quot;.files&quot;"
date: 2013-06-14
forum: Programming Talk
---

### Post by Rahul04789 on 2013-06-14
Hi All,

I was trying to delete all the directories whose names end with ".files" using find command as:

 find ~ -name "*.files" -delete


but following error came:

find: cannot delete `/home/rahul/Music/amitabh hits/32. Naseeb-Zindagi Imtihaan Leti Hai (Kamlesh, Awasthi, Anwar.wma.files': Directory not empty


Is there any command to delete a directory which is not empty, using find or any other unix command.

Thanks in advance.... :)

---

### Post by alan9800 on 2013-06-14
try this:```
[COLOR=#000000]find ~ -name "*.files" -exec rm -rf {} \;[/COLOR]
```

---

### Post by prodigy_ on 2013-06-14
```
find $HOME -type d -name "*.files" -exec rm -rf '{}' +
```
Note: **rm -rf** is inherently dangerous (since it removes folders and files recursively) so be careful.

---

### Post by CharlesA on 2013-06-14
> **prodigy_ said:**
> ```
find $HOME -type d -name "*.files" -exec rm -rf '{}' +
```
Note: **rm -rf** is inherently dangerous (since it removes folders and files recursively) so be careful.

Yep. It would probably be a better idea to run this first:

```
find $HOME -type d -name "*.files" -print
```

---

### Post by alan9800 on 2013-06-15
the following code should be more secure:```
find $HOME -type d -name "*.files" -exec rm -Irv '{}' \;
```

---

### Post by sisco311 on 2013-06-15
Also the -name test should come before the -type test in order to avoid having to test every file if it's a directory or not. ;)

---

### Post by Rahul04789 on 2013-06-15
Hey Thanks all, Got my problem solved

---

