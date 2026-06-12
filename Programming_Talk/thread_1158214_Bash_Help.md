---
title: "Bash Help"
date: 2009-05-13
forum: Programming Talk
---

### Post by prem1er on 2009-05-13
Writing a bash script to standardize some accounts and I would like to know if there is a way to do these two commands without using the temp file that I currently have.  Is there a way to sort the file and remove white space all into one file without the need for a temp?

```
sort $_temp > $_db2_sorted
rm $_temp

cat $_db2_sorted | sed 's/ //g' | sort > $_temp
rm $_db2_sorted
```

---

### Post by monkeyking on 2009-05-13
Just to clarify the steps.

1. you sort the file using 'sort',
2. you remove all whitespace.
3. you sort it again?

---

### Post by prem1er on 2009-05-13
Sorry, a coworker just helped me and I corrected my mistake without editing this post.

This is what I was looking for.  Sorry again.

```
cat $_temp | sed 's/ //g' | sort > ${_sortDataArray[$_index]}
```

---

