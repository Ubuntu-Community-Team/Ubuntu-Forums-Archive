---
title: "egrep: The parameter or environment lists are too long."
date: 2008-02-04
forum: Programming Talk
---

### Post by G|N| on 2008-02-04
Hello,

I am writing a little bash script with an egrep expression.
The egrep command has to parse a lot of files and in some directories i get this error:
```

/usr/bin/egrep: The parameter or environment lists are too long.

```

How can i make the list use more files?

This is the expression:
 [PHP]egrep -i  '(DEF|DEFINE).*TEMP-TABLE.*' *.i  > $TEMP_FILE[/PHP]

---

### Post by Amit Yaron on 2008-02-04
Use a 'for' loop:

for file *.i
do
  egrep -i  '(DEF|DEFINE).*TEMP-TABLE.*' $file >> $TEMP_FILE
done

---

