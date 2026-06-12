---
title: "can someone write me a bash script?"
date: 2006-04-11
forum: Programming Talk
---

### Post by iwra on 2006-04-11
not asking a lot.  just a simple script that will rename files into numbers.

i need a script that will be able to take the below:

a125.foo
b126.foo
c127.foo
d128.foo
e129.foo
f130.foo
g131.foo
h132.foo
i133.foo
j134.foo

and turn them into:

01.foo
02.foo
03.foo
04.foo
05.foo
06.foo
07.foo
08.foo
09.foo
10.foo

it has to be double digits.  otherwise, it would just become: 1, 10, 2, 3, etc.

thanks for the help.

---

### Post by Drakx on 2006-04-11
here you go [http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/) :)

---

### Post by souki on 2006-04-11
change the sprintf format as you want it (%02d if you want 2 digits)
and of course the extension

run once, then un-comment the 'mv' command
```
#!/bin/sh

ext=foo
i=0
FILES=`ls *.$ext`

for file in $FILES
do
	if [ -f $file ]
	then
		let "i+=1"
		num=`printf "%06d" $i` 
		dest=`echo "$file" |sed -e "s/.*\.$ext$/$num.$ext/"`
		echo "$file => $dest"
		#mv "$file" "$dest"
	fi
done
```

---

### Post by bmosov01 on 2010-05-02
Nice!  Just the script I was looking for.  Thanks Souki.

---

### Post by soltanis on 2010-05-03
Pop a python?

```

#!/usr/bin/env python
import glob, os

i = 0
for file in glob.glob("*.foo"):
  os.rename(file, "%02d.foo" % i)
  i += 1

```

Always found that more readable than bash scripts somehow.

---

### Post by slavik on 2010-05-03
> **soltanis said:**
> Pop a python?

```

#!/usr/bin/env python
import glob, os

i = 0
for file in glob.glob("*.foo"):
  os.rename(file, "%02d.foo" % i)

```

Always found that more readable than bash scripts somehow.
does that increment i?

---

### Post by DaithiF on 2010-05-06
a variant on the previous bash solution:
```
ls *.foo | nl | while read number file; do echo mv "$file" "$(printf "%02d" $number).${file##*.}"; done

```
and as before, take out the echo when ready to run for real

---

### Post by soltanis on 2010-05-06
> **slavik said:**
> does that increment i?

Now it does. Oh how many files I've clobbered with mistakes like that.

---

