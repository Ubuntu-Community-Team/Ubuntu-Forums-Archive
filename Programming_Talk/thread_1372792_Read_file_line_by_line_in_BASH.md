---
title: "Read file line by line in BASH"
date: 2010-01-04
forum: Programming Talk
---

### Post by Tristanm1 on 2010-01-04
I am attempting to delete duplicate files. Using fdupes, I've generated a file that lists the full path of all duplicate files (excluding one copy of each file). Now what I need to do is read from this file so that I can use each filepath with the rm command. I am unsure how to do this, however. Could someone help me with this problem?

---

### Post by falconindy on 2010-01-04
```
while read file; do
  rm "$file"
done < /path/to/dupe.list
```

---

### Post by Tristanm1 on 2010-01-05
That works, thanks. The blank lines in the file throw back an error with rm, but that is fine.

---

### Post by iMisspell on 2010-01-05
> **Tristanm1 said:**
> That works, thanks. The blank lines in the file throw back an error with rm, but that is fine.


This is untested, but im pretty sure it will work...
```


while read file; do
  # check if file exists, if so, then delete...
  if [[ -e "$file" ]] ; then
    rm "$file"
  fi
done < /path/to/dupe.list


```

---

