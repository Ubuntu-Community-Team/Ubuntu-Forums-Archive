---
title: "bash: reading line by line"
date: 2007-07-26
forum: Programming Talk
---

### Post by jmc1024 on 2007-07-26
I'm trying to process a file with bash.  I'm using the following code:
```
exec < /tmp/answers
while read line
do
   echo $line was selected
done

```
If the file has a final line with just a new line, then it get echoed. However if the last line has text followed by a new line then the text is _not_ echoed. Can anyone explain why this is?
Thanks,
Mark

---

### Post by meatpan on 2007-07-26
I tried recreating your example, and could not reproduce the issue.

With an input file of ( added the \n's to mark my newlines.  Verified this is correct with `cat -e`):
foo\n
bar\n
hey\n

The output was:
foo was selected
bar was selected
hey was selected

With an input file of:
foo\n
bar\n
hey\n
\n

The output was:
foo was selected
bar was selected
hey was selected
was selected

Am I missing the problem?

---

### Post by jyba on 2007-07-26
I wonder if the OP actually intended to say "if the last line has text **not **followed by a new line then the text is **not** echoed".

```
foo\n
bar\n
hey

The output is:
foo was selected
bar was selected
```

If so, I think it is because the bash builtin 'read' returns zero unless end-of-file is encountered. So on the last line it encounters some text and then the end-of-file and returns non-zero.

The first line of the loop really means "while 'read line' returns zero" execute the following commands. In this case 'read line' returns non-zero, so the action 'echo $line....' never gets executed.

---

### Post by meatpan on 2007-07-27
Good point.  That said, a methodology to produce what the OP wants is:

```

#!/bin/bash

exec < test_script1_in.txt
while read line
do
    if [ "$line" != "" ]; then
	echo $line was selected
    fi
done

```

The conditional statement ignores empty lines.   Don't give up, OP!

Verified to output:
foo was selected
bar was selected
hey was selected

from the input:
foo\n
bar\n
hey\n
\n

---

### Post by jmc1024 on 2007-08-01
Thanks for your help.  I'm trying to use whiptail in an install script.  When using the whiptail checklist, the checked items are written to stdout space separated:
"a" "c" "d" "f" "g"
so I used sed to turn that into:
"a"\n
"c"\n
"d"\n
"f"\n
"g"\n
\n
I'm using meatpan's code and have it working.
Thanks, Mark

---

