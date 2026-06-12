---
title: "Search and replace with AWK truncates"
date: 2009-01-28
forum: Programming Talk
---

### Post by SmiKK on 2009-01-28
Hello! Why does this command to search and replace a string also truncate the file? The actual replacement does work.

```
cp /var/log/dmesg .
cat dmesg | wc -l
**$ 300**
awk '{gsub("IPv6","IPv7");print > FILENAME}' dmesg
cat dmesg | wc -l
**$ 60**

```

---

### Post by stylishpants on 2009-01-28
You are iterating through the file line-by-line, while simultaneously writing lines to the file.

This is something to avoid.
```

# using awk:
awk '{gsub("IPv6","IPv7"); print}' dmesg > file
mv file dmesg

# in-place edit, using sed:
sed -i 's/IPv6/IPv7/g' dmesg


# in-place edit, using perl:
perl -pi -e 's/IPv6/IPv7/g' dmesg
```

---

