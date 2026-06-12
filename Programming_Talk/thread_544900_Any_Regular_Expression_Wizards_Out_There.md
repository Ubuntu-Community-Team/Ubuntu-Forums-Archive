---
title: "Any Regular Expression Wizards Out There?"
date: 2007-09-06
forum: Programming Talk
---

### Post by nchase on 2007-09-06
I'm trying to search through a file for strings that start with a variable and end at a quotation mark. I'd like to print every instance of such a string.

Is such a thing possible?

Example: My variable in this example is **x** if I had a file containing ```
"gee, this sure is a difficult problem for me," said xavier. "Why can't it be easier to fix this xylophone?" 
```

I would want it to print:
```
Xavier. 
```
and...
```
x this xylophone?
```

Again, is this possible?

---

### Post by slavik on 2007-09-06
[xX].*[\.\?!] (off the top of my head, but likely wrong)

---

### Post by Cappy on 2007-09-06
```

grep -io 'xorwhateverwordyouwanttofind[^"]*' filenamehere

```

Take off the -i if you don't want case-insensitivity

---

### Post by ghostdog74 on 2007-09-06
you don't have to use regular expressions if you are not familiar. until you do: there's a standard algo to do what you want. 
```

awk 'BEGIN{FS=""}
{
        for(i=1;i<=NF;i++){  #go through every character
            if ( $i ~ /[xX]/) {flag=1} #if hits x or X set a flag
            else if ( $i ~ /\"/ ){flag=0}  # if hits ", remove flag
            if (flag){ printf $i} #only prints if flag is set
        }
        print ""
}' "file"

```
output:
```

# ./test.sh
xavier. x this xylophone?

```
if you are in for the regexp path
```

#!/usr/bin/python
import re
data=open("file").read()
pat=re.compile("([xX].*?)\"",re.M|re.DOTALL)
print ' '.join(pat.findall(data))

```
output:
```

 # ./testing.py
xavier.  x this xylophone?

```

---

