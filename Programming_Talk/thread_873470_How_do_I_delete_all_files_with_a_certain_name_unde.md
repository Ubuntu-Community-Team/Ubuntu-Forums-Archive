---
title: "How do I delete all files with a certain name under subdirectories?"
date: 2008-07-29
forum: Programming Talk
---

### Post by SNYP40A1 on 2008-07-29
I want to delete all files with a specific name found below some subdirectory?  Does anyone know a command to do this (I prefer to keep all other files :-)  I think it will involve the find command, but not sure how to chain it to delete.

---

### Post by mssever on 2008-07-29
> **SNYP40A1 said:**
> I want to delete all files with a specific name found below some subdirectory?  Does anyone know a command to do this (I prefer to keep all other files :-)  I think it will involve the find command, but not sure how to chain it to delete.
```
rm */filename   #or
rm dir{1,2,3}/filename   #or
for i in *; do
    [[ -d "$i" ]] && rm "$i"/filename
done
```

---

### Post by ghostdog74 on 2008-07-29
```

find /path -type f -name "filename" -delete

```

---

### Post by SNYP40A1 on 2008-07-29
> **ghostdog74 said:**
> ```

find /path -type f -name "filename" -delete

```

Thanks, this also works:

find . -name "dcc*" -delete

Not sure why the -type f is needed.

---

### Post by ghostdog74 on 2008-07-29
see the man page for definition of -type f

---

### Post by Martin Witte on 2008-07-29
> **SNYP40A1 said:**
> Thanks, this also works:

find . -name "dcc*" -delete

Not sure why the -type f is needed.

'-type f' is needed if you just want to delete regular files, and not eg. directories

---

