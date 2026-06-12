---
title: "simple bash script error catch error codes"
date: 2007-02-24
forum: Programming Talk
---

### Post by monkeyking on 2007-02-24
I have a command I want to run, and in a terminal it goes like this.
```

wc -l test_folder/files*

```
This runs perfectly, even though it tells me that it alsa matches a folder.
I've made a script that runs the above code.
it looks like.

```

#!/bin/bash
wc -l test_test_folder/files*
wc -l test_folder5/out*

```

So I guess the problem is that the wc command treats a match on a directory as an error,
but when it runs from the commandline itself, it just continues. While the bash scripts stops executing.



Thanks in advance

---

### Post by Enselic on 2007-02-24
If you pasted the exact file, you have a type in it (or the example).

Shouldn't it be
```

#!/bin/bash
wc -l test_folder/files*
wc -l test_folder5/out*
```

?

I tried this, and the error does not seem to break the script.

---

### Post by monkeyking on 2007-02-25
ok I had a typo,
so I'll elaborate.

if I type
```

wc -l test_effekt5/risk*.*

```
Then I get
```

1000 test_effekt5/risk0.out
1000 test_effekt5/risk10.out
1000 test_effekt5/risk1.out
1000 test_effekt5/risk2.out
1000 test_effekt5/risk3.out
1000 test_effekt5/risk4.out
1000 test_effekt5/risk5.out
1000 test_effekt5/risk6.out
1000 test_effekt5/risk7.out
1000 test_effekt5/risk8.out
1000 test_effekt5/risk9.out

```
Which is excatly what I want from this script prinln.sh
```

#!/bin/bash

wc -l test_effect5/risk*.*

```
Outputs the following
```
wc: test_effect5/risk*.*: No such file or directory

```
thanks in advance

---

