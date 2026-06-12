---
title: "What's the first of the five' file permission numerical mode digits?"
date: 2013-09-16
forum: New to Ubuntu
---

### Post by sl3ax on 2013-09-16
By doing for example in a file
```

chmod 00755 file

```

What does the first zero indicates?
Thanks. :)

---

### Post by sisco311 on 2013-09-16
[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

---

### Post by sl3ax on 2013-09-17
> **sisco311 said:**
> [http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)
Sorry, I can't find that information in the link. :(

---

### Post by Lars Noodén on 2013-09-17
If there are 5 digits instead of 4, it is probably a typo.  With 4 digits, the first one has to do with set GID, set UID, and sticky bit for [file permissions](https://help.ubuntu.com/community/FilePermissions).  You can see them in detail for any given file using [stat](http://manpages.ubuntu.com/manpages/raring/en/man1/stat.1.html).

```

stat /etc/apt/sources.list

```

---

### Post by sl3ax on 2013-09-17
> **Lars Noodén said:**
> If there are 5 digits instead of 4, it is probably a typo.  With 4 digits, the first one has to do with set GID, set UID, and sticky bit for [file permissions]("https://help.ubuntu.com/community/FilePermissions").  You can see them in detail for any given file using [stat]("http://manpages.ubuntu.com/manpages/raring/en/man1/stat.1.html").

```

stat /etc/apt/sources.list

```
I think it's not a typo because I found it in many books. :confused:

---

### Post by steeldriver on 2013-09-17
AFAIK the chmod program can only access the lower 4 octal digits (i.e. up to the setuid / setgid / sticky bit) however the higher bits in the mask are used by the internal stat structure to indicate things like whether it is a regular file / block device / FIFO / link and so on. In particular **4**0000 is the directory mask - see 

```
man 2 stat
```

for details

---

### Post by sl3ax on 2013-09-17
> **steeldriver said:**
> AFAIK the chmod program can only access the lower 4 octal digits (i.e. up to the setuid / setgid / sticky bit) however the higher bits in the mask are used by the internal stat structure to indicate things like whether it is a regular file / block device / FIFO / link and so on. In particular **4**0000 is the directory mask - see 

```
man 2 stat
```

for details
Thanks.:D

---

