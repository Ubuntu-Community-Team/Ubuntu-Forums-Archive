---
title: "Shell Programming Question"
date: 2009-01-26
forum: Programming Talk
---

### Post by Tek-E on 2009-01-26
How....can I read input from a user character by character. Then place each character from the string the user entered into their own variables?

Any help with this will be greatly appreciated!

Thank you!

---

### Post by avikrc on 2009-01-26
Hi,
you could use the cut utility to achieve this..

[assuming of course you already know how many characters the user will enter]

echo "Enter your name: "
read name
echo "You entered: $name"
a=`echo $name|cut -c 1-1`
b=`echo $name|cut -c 2-2`
c=`echo $name|cut -c 3-3`
d=`echo $name|cut -c 4-4`

echo "$a $b $c $d"
echo ""

---

### Post by geirha on 2009-01-26
You can have the read command only read 1 character at a time with -n 1.
```

#!/bin/bash
read -n1 a
read -n1 b
echo $a $b

```

On the other hand, if you just want to process a string character by character, you can do:

```

#!/bin/bash
read word
for ((i=0; i < ${#word}; i++)); do 
    echo "index $i: ${word:i:1}";
done

```

---

### Post by Tek-E on 2009-01-26
Thank you both Very much!

---

