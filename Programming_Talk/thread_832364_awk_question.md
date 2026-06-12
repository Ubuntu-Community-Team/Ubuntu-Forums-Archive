---
title: "awk question"
date: 2008-06-17
forum: Programming Talk
---

### Post by maybeway36 on 2008-06-17
How can I print all fields $3 and higher? In other words, I want to print everything but $1 and $2.

---

### Post by Phenax on 2008-06-17
Use a for loop -- NF represents the number of fields in the line.

```

$ echo "first second third fourth fifth sixth" | awk '{ for (i=3; i<=NF; i++) print $i }'
third
fourth
fifth
sixth

```
If you don't want newlines, you can use printf.
```

$ echo "first second third fourth fifth sixth" | awk '{ for (i=3; i<=NF; i++) printf("%s ", $i) }'
third fourth fifth sixth

```

---

### Post by ghostdog74 on 2008-06-17
make $1 and $2 null
```

awk '{$1=$2=""}1' file

```

---

