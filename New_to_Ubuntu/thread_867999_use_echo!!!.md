---
title: "use echo!!!"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by ra2008 on 2008-07-23
Hi,
i am trying to create new file using "echo" and write in a new line. what i do is:

$echo -e 1 \n 2 >> test

what i get inside test:
1 n 2 
any hint?

---

### Post by Xerp on 2008-07-23
Not all versions of echo permit backslash escape codes.

```

echo "one line" > file
echo "new line" >> file

```

---

### Post by Cypher on 2008-07-23
You need to put the expression in quotes to properly evaulated. So change your line to
```

echo -e "1\n2" > test
cat test

```

---

