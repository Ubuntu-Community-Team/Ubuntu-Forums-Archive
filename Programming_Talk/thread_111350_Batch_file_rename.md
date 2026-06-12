---
title: "Batch file rename"
date: 2006-01-02
forum: Programming Talk
---

### Post by DaMasta on 2006-01-02
I need to rename all my mp3s with underscores instead of spaces. I have this script which will rename all the files ending in mp3 from spaces to underscores within a directory. I have about 300 albums though so doing it directory by directory is very tedious. How can I change this script to do it recursively? Thanks.

```
for i in $(ls -1 *)
do
  rename 's/\ /_/' *.$1
done
```

---

### Post by meborc on 2006-01-02
maybe that helps: [http://ubuntuforums.org/archive/index.php/t-98147.html](http://ubuntuforums.org/archive/index.php/t-98147.html)

---

### Post by toojays on 2006-01-02
Use the 'find' utility:```
find . -type f -execdir rename 's/\ /_/' '{}' ';'
```

---

### Post by DaMasta on 2006-01-02
Thanks guys.

---

