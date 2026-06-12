---
title: "Search a directory of text docs and delete a certain word from them all"
date: 2010-03-08
forum: Programming Talk
---

### Post by bradley002 on 2010-03-08
I know how to search a directory of files for a term (grep "term" -r ./Directory), but is there a way to remove it from each file it is found in? I looked at the tr command, but am not sure if it is the right one to use. Thanks.

---

### Post by Barriehie on 2010-03-08
> **bradley002 said:**
> I know how to search a directory of files for a term (grep "term" -r ./Directory), but is there a way to remove it from each file it is found in? I looked at the tr command, but am not sure if it is the right one to use. Thanks.

Gawk/awk may be what you're looking for.  It's a stream editing language and I think awk comes installed.  I like gawk and it has to be installed.

HTH

---

### Post by kaibob on 2010-03-08
> **bradley002 said:**
> I know how to search a directory of files for a term (grep "term" -r ./Directory), but is there a way to remove it from each file it is found in? I looked at the tr command, but am not sure if it is the right one to use. Thanks.

Sed is a good tool for this job. The following command removes all instances of "string" from file. For multiple files, a simple loop can be used.

```
sed -i 's/string//g' file
```

The -i option tells sed to overwrite file. If this is not desired, you can omit the -i option and redirect the output to a new file.

---

### Post by bradley002 on 2010-03-08
Excellent. I did want to overwrite the file, and everything went smoothly. :)

---

