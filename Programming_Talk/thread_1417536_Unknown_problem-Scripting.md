---
title: "Unknown problem-Scripting"
date: 2010-02-27
forum: Programming Talk
---

### Post by hakermania on 2010-02-27
Even if I type 1 or 2 it goes to *) and not to 1) or 2)
Why?
```
#!/bin/sh
echo "Type some text"
read STR_ORIGINAL
echo "
1= Lower to upper
2= Upper to lower"
read what
case $what in
		1)
STR_UPPER=`echo $STR_ORIGINAL | tr a-z A-Z`
echo "
$STR_UPPER";;
		2)
STR_LOWER=`echo $STR_ORIGINAL | tr A-Z a-z`
echo "
$STR_LOWER";;
		*)
a=1
lol=5
while [ "$a" != "$lol" ]
do
clear; echo "ERROR"; sleep 0.2; clear; echo "ERROR."; sleep 0.2; clear; echo "ERROR.."; sleep 0.2; clear; echo "ERROR..."; sleep 0.2; 
a=`expr $a + 1`
done
clear;
esac
```

. . .Any help?;)?

---

