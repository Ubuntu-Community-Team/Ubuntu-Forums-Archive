---
title: "Read format? double spacing?"
date: 2010-07-12
forum: Programming Talk
---

### Post by unrealer on 2010-07-12
Hello all, I have questions related to bash again. As you can see, I'm terrible at programming. I have this text file with comment lines, however the numbers are used for other programs, but as it is now, it's unusable because the other program requires 2 comment line per block of numbers as well as double spacing between each of the exponentials. 


INPUT
comment line
 0.00000E+00 0.00000E+00 0.00000E+00 0.00000E+00 0.00000E+00 1.87656E+00 0.00000E+00 0.00000E+00
 0.00000E+00 0.00000E+00 0.00000E+00 0.00000E+00 0.00000E+00 1.34392E-01-4.96945E-04 0.00000E+00
 0.00000E+00 0.00000E+00 0.00000E+00 0.00000E+00 0.00000E+00 0.00000E+00-1.12614E-05 0.00000E+00
comment line
 0.00000E+00 0.00000E+00 0.00000E+00 0.00000E+00 0.00000E+00 1.34958E+00 0.00000E+00 0.00000E+00
 0.00000E+00 0.00000E+00 0.00000E+00 0.00000E+00 0.00000E+00 3.63471E-02-5.37598E-04 0.00000E+00
 0.00000E+00 0.00000E+00 0.00000E+00 0.00000E+00 0.00000E+00 0.00000E+00-1.33741E-07 0.00000E+00

DESIRED OUTPUT
comment line
comment line
  0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  1.87656E+00  0.00000E+00  0.00000E+00
  0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  1.34392E-01 -4.96945E-04  0.00000E+00
  0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00 -1.12614E-05  0.00000E+00
comment line
comment line
  0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  1.34958E+00  0.00000E+00  0.00000E+00
  0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  3.63471E-02 -5.37598E-04  0.00000E+00
  0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00 -1.33741E-07  0.00000E+00

anyone have any ideas?

Thanks for all the help

PS some how it wouldn't allow me to add 2 spaces between each of the numbers.

---

### Post by gmargo on 2010-07-12
Perl one-liner.
```

$ cat in.txt
comment line
0.00000E+00 0.00000E+00 0.00000E+00 0.00000E+00 0.00000E+00 1.87656E+00 0.00000E+00 0.00000E+00
0.00000E+00 0.00000E+00 0.00000E+00 0.00000E+00 0.00000E+00 1.34392E-01-4.96945E-04 0.00000E+00
0.00000E+00 0.00000E+00 0.00000E+00 0.00000E+00 0.00000E+00 0.00000E+00-1.12614E-05 0.00000E+00
comment line
0.00000E+00 0.00000E+00 0.00000E+00 0.00000E+00 0.00000E+00 1.34958E+00 0.00000E+00 0.00000E+00
0.00000E+00 0.00000E+00 0.00000E+00 0.00000E+00 0.00000E+00 3.63471E-02-5.37598E-04 0.00000E+00
0.00000E+00 0.00000E+00 0.00000E+00 0.00000E+00 0.00000E+00 0.00000E+00-1.33741E-07 0.00000E+00

$ cat in.txt | perl -pe 'if (/^\d/) {s/ /  /g} else {print $_}'
comment line
comment line
0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  1.87656E+00  0.00000E+00  0.00000E+00
0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  1.34392E-01-4.96945E-04  0.00000E+00
0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00-1.12614E-05  0.00000E+00
comment line
comment line
0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  1.34958E+00  0.00000E+00  0.00000E+00
0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  3.63471E-02-5.37598E-04  0.00000E+00
0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00-1.33741E-07  0.00000E+00

```

---

### Post by unrealer on 2010-07-12
sorry, but I really don't know any perl, is there python one liner equivalent?

---

### Post by gmargo on 2010-07-12
Here's an equivalent script in python.  Put it in a file and make it executable.  Adjust as needed.

```

#!/usr/bin/python
# vim: set ts=8 sts=4 sw=4 et :

import sys
import re

for line in sys.stdin:
    if re.search("^\d", line):
        sys.stdout.write(line.replace(" ","  "))
    else:
        sys.stdout.write(line)  # print original line
        #sys.stdout.write("\n")  # followed by a blank line
        sys.stdout.write(line)  # or a duplicate of the original line

```

---

### Post by unrealer on 2010-07-13
thanks for the reply, however, the solution still doesn't solve the issue where the negative scientific notation is touching the previous number, thus python locate it using space.. I was wondering if python have some sort of read format.

---

### Post by geirha on 2010-07-13
Gave it a go with sed...
```
$ sed -e '/^[0-9+-]/s/ /  /g' -e '/\([+-][0-9][0-9]\)-/s//\1 -/g' -e '/^[0-9+-]/!p' input
comment line
comment line
0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  1.87656E+00  0.00000E+00  0.00000E+00
0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  1.34392E-01 -4.96945E-04  0.00000E+00
0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00 -1.12614E-05  0.00000E+00
comment line
comment line
0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  1.34958E+00  0.00000E+00  0.00000E+00
0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  3.63471E-02 -5.37598E-04  0.00000E+00
0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00  0.00000E+00 -1.33741E-07  0.00000E+00

```

Though, can't you just fix the program that outputted this broken data?

---

### Post by wmcbrine on 2010-07-13
You could use a regex, or you could break up the line at fixed intervals if the format is rigid enough -- which it seems to be in this case, if I can go by the example.

Here's one way to convert a single line to the doubly-spaced format in Python:

```
' '.join([line[i:i + 12] for i in range(0, len(line), 12)])
```

That's not a whole program, but it's the important bit.

BTW, when you want to preserve spacing on this forum, put "code" tags around the text.

---

