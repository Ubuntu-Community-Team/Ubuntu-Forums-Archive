---
title: "How to remove first block section from text file in Linux bash?"
date: 2015-12-15
forum: Programming Talk
---

### Post by abcuser on 2015-12-15
Hi,
on Ubuntu 14.04 I have the following file:
```

BEGIN
line_1
line_2
END
BEGIN
line_3
END
BEGIN
line_4
line_5
line_6
END

```

Note: Between BEGIN...END section there can be at least one or many line_x.

I would like to remove first BEGIN...END block? The result should be:
```

BEGIN
line_3
END
BEGIN
line_4
line_5
line_6
END

```
How to write such a code in Linux bash shell?
Thanks

---

### Post by abcuser on 2015-12-15
I have figured out one of the solution:
```
sed -n '/BEGIN/,/END/p' data.txt | sed ':a;N;s/\n/*/g;ba' | sed 's/END*/END\n/g' | sed '1d' | sed 's/*/\n/g' | sed '/^$/d' > out.txt
```
Note: The "*" should not exists in sample data and in my case never exists.

Is there any simpler solution?

---

### Post by Bucky Ball on 2015-12-15
*Thread moved to **Programming Talk**.*

---

### Post by steeldriver on 2015-12-15
You could use csplit

```

csplit file %END%+1

```

(skip to the first occurrence of pattern END, and then one further line). The output will go by default to a file called 'xx00'.

---

