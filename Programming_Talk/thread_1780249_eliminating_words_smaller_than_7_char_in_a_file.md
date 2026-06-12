---
title: "eliminating words smaller than 7 char in a file"
date: 2011-06-11
forum: Programming Talk
---

### Post by Mia_tech on 2011-06-11
guys, I have a file which contains passwords, and I want to eliminate those who are smaller than 7 chars, for this I've created a while loop, but I'm kind of stuck in the condition.... here's what I've got so far

```
while read line
do
   #condition would go here to test if line is greater or smaller than 7 char
   echo $line >> newfile.txt
done < file.txt
```

any help appreciated

thanks

---

### Post by Arndt on 2011-06-11
> **Mia_tech said:**
> guys, I have a file which contains passwords, and I want to eliminate those who are smaller than 7 chars, for this I've created a while loop, but I'm kind of stuck in the condition.... here's what I've got so far

```
while read line
do
   #condition would go here to test if line is greater or smaller than 7 char
   echo $line >> newfile.txt
done < file.txt
```

any help appreciated

thanks

A bit primitive, but it works:

```
grep '........'
```

---

### Post by BkkBonanza on 2011-06-11
You need,
```

if [[ ${#line} -ge 7 ]]; then
  echo $line >> newfile.txt
fi

```

---

