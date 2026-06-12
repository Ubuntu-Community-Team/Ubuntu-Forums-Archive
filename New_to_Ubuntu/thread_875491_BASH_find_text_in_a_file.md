---
title: "BASH find text in a file"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by DBrocks on 2008-07-30
Hey guys. what is the code to find a string of text in a file, and if it finds it, echo "found"

---

### Post by iaculallad on 2008-07-30
> **DBrocks said:**
> Hey guys. what is the code to find a string of text in a file, and if it finds it, echo "found"

You could use grep, as in:

> cat /boot/grub/menu.lst | grep kernel

But would not issue the string "found" instead it issues the "kernel" string you want it to locate.

---

### Post by DBrocks on 2008-07-30
Basically I want to make it into an If/then statement. How would I do that?

---

### Post by InfinityCircuit on 2008-07-30
```
if grep -q PATTERN FILE; then
    echo "Found"
fi
```

---

### Post by ghostdog74 on 2008-07-30
there's no need to use cat because grep takes in  a file
```

grep "string" file && echo "found"

```

---

### Post by DBrocks on 2008-07-30
Infinity, that worked. thanks so much!

---

### Post by justinhj on 2008-07-30
This works for me. Save the code as found.sh

Then 

chmod +x found.sh

found.sh filename text

```
#/usr/bin/bash

if [ -z "$2" ]
then
    exit
fi

if [ -e "$1" ]
then
    count=`egrep -ic "$2" "$1"`

    if [ $count -gt 0 ]
    then
	echo found
    fi
fi

```

---

