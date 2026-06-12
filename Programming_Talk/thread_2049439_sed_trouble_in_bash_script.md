---
title: "sed trouble in bash script"
date: 2012-08-28
forum: Programming Talk
---

### Post by conradin on 2012-08-28
Hi all, 
I want to bring up a line of text one line at a time, I thought, and easy enough task for sed. The wc bit makes the count whatever the number of lines is. 
I get the error:"sed: -e expression #1, char 3: unknown command: `.'"
also, how can I separate the variable "i" from the sed argument "p"?  I am wondering if a space or lack of space is causing the issue. Ive tried both, neither work. 

Can someone point out how to fix this?
But I get an error, I cant seem to figure out. 
```

#!/bin/bash 
set -vx
sometime=5
length=`wc -l someFile | grep -o *[0-9]`

for i in {1..$length..1}
do
 	sed -n $ip someFile
sleep $sometime
done
```

---

### Post by Bachstelze on 2012-08-28
For your last question, you can use quotes:

```
firas@aoba:~$ i=foo
firas@aoba:~$ echo "$i"p
foop

```

---

### Post by sisco311 on 2012-08-28
Check out BashFAQ 001, 082, 011 and [http://mywiki.wooledge.org/BraceExpansion](http://mywiki.wooledge.org/BraceExpansion)

```


while read -r line
do
    printf '%s\n' "$line"
    sleep 5
done < filename


```

---

### Post by conradin on 2012-08-30
Thanks sisco! That helps!

---

