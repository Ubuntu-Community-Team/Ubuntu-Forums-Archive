---
title: "shellscript question variable assignment"
date: 2008-11-21
forum: Programming Talk
---

### Post by pedrotuga on 2008-11-21
Can anybody tell me what am I doing wrong in here:

```
#!/bin/sh
while [ "$condition" != "/QUIT" ]
do
	read condition
	condition = `echo $condition | tr "[:lower:]" "[:upper:]"` #esta linha dá caldo :S
	echo $condition
done
```
?

I am getting this message:
```
asd
./nctest.sh: 9: condition: not found
asd
aaa  
./nctest.sh: 9: condition: not found
aaa
```

---

### Post by Airr on 2008-11-21
Remove the space before and after the equal sign in the "condition = " line.

AIR.

---

