---
title: "cleanup script"
date: 2009-05-28
forum: Programming Talk
---

### Post by vixducis on 2009-05-28
Hi,

To come right to the point: I need a script that deletes every file that doesn't have flac as extension and then deletes all the empty folders. I already read a file about shell scripting, and i learned the basics, but i just can't find a good solution. Can somebody make it or give me some hints?

Thanks,
Vixducis

---

### Post by ghostdog74 on 2009-05-28
check out the find command. man find
```

find /path -type f ! -name "*.flac" <continue>

```

---

### Post by johnl on 2009-05-28
Hi,

here's a hint.

The following will give you a list of all files in "$DIR" that do not have ".flac" in their names (case insensitive):

```

find "$DIR" -type f | grep -i -v ".flac" |
while read file ; do
    echo "$file"
done

```

---

### Post by johnl on 2009-05-28
> **ghostdog74 said:**
> check out the find command. man find
```

find /path -type f ! -name "*.flac" <continue>

```

I swear I looked for a 'not' operator to find. Thanks for posting this, I learned something :)

---

### Post by vixducis on 2009-05-28
Since there will be a maximum of 3 levels of subdirectories, i made this code (probably can be more efficient with a loop checking if there are empty subdirectories. It works, thanks for your help.

```
find . -type f ! -name '*.flac' -exec rm -f {} \;
find . -type d -empty -exec rm -rf {} \;
find . -type d -empty -exec rm -rf {} \;
find . -type d -empty -exec rm -rf {} \;
```

---

