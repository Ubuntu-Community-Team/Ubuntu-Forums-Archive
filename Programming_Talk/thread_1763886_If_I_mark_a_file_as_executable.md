---
title: "If I mark a file as executable"
date: 2011-05-21
forum: Programming Talk
---

### Post by ki4jgt on 2011-05-21
If I mark a .py file as executabe (Change the bit) does the file itself have the bit changed, or do everyone of my users have to do this themselves?

---

### Post by NovaAesa on 2011-05-21
Permissions are a filesystem level concept rather than a file concept. When you change permissions to allow execution, the file itself doesn't change.

As for whether or not the users will have to set the permissions themselves... that really depends on how you distributed the files.

---

### Post by hakermania on 2011-05-21
I think this shows that nothing actually changes at the file when adding the executable bit:
```

alex@MaD-pc:~$ md5sum a
**bc7ac49d5c15a28d7c43b05aa7960ec7  a**
alex@MaD-pc:~$ chmod +x a
alex@MaD-pc:~$ md5sum a
**bc7ac49d5c15a28d7c43b05aa7960ec7  a**
```

---

### Post by ve4cib on 2011-05-22
For users on the local machine the file will be marked as executable, since as Nova pointed out, file permissions are a file-system level thing.

Also note that there are in fact 3 executable bits: Owner, Group, and Other.  If only the Owner executable bit is true then only the owner of the file can execute the file.  Nobody else can.  Likewise, if only group are both true then only users that are part of the same group as the file could execute it.

---

