---
title: "How add to two steps to validation on structure if and execute a calculate .sh"
date: 2017-08-18
forum: New to Ubuntu
---

### Post by sed_faster on 2017-08-18
Hello folks,

I am trying put this code run but I can't!
```

if [ (i>=g) -ge ((i%g == 0)); ]

```

letter i and g this is a variable which receive number inside a loop for. To do the calculate I need this piece of code:
```

((i%g == 0));

```
I really tested this piece script only and this do what I need. But, if I add the validation -ge (greater than or equal) the script don't run. I receive this message:
> 
./2.sh: line 20: syntax error near unexpected token `i'
./2.sh: line 20: `              if [ (i>=g) -ge ((i%g == 0)); ]'


How can I fix this?
Thanks

---

### Post by steeldriver on 2017-08-18
What is the expression intended to test, and what shell are you using?

---

### Post by sed_faster on 2017-08-18
How can I see more information about my shell?
I intend compare two number and discovery if **i** is equal or greater than **g** [SIZE=6]**and**[/SIZE] if i%g==0.

thanks

---

### Post by steeldriver on 2017-08-18
If you are writing a script, use a "shebang" line at the top to indicate what shell should be used

```

#!/bin/bash

```

In modern bash shells, the recommended syntax for arithmetic evaluation uses double parentheses e.g.

```

if ((i>=g && i%g == 0)); then echo "Yes"; fi

```

---

### Post by sed_faster on 2017-08-18
On script I use this  this shebang: 
```

#!/bin/bash

```
What means a shebang?

How can I know when use a single parentheses or double parentheses? And I can switch && to -a ?

---

### Post by steeldriver on 2017-08-18
"shebang" (or "hashbang") just refers to the two characters # and ! at the start of the line - see for example [Shebang (Unix)](https://en.wikipedia.org/wiki/Shebang_(Unix))

Really there's no short-cut to knowing the right syntax - you just need to study the documentation and try stuff - you *could* use older (POSIX-compatible) syntax such as

```

if [ $i -ge $g -a $(expr $i % $g) -eq 0 ]; then echo "Yes"; fi

```

which should work in /bin/sh as well as /bin/bash

---

