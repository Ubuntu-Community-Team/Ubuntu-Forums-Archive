---
title: "what does 2&gt;&amp;1(1&gt;&amp;2) mean?"
date: 2011-09-30
forum: New to Ubuntu
---

### Post by node2network on 2011-09-30
I'm user of Ubuntu10.04 and bash.

2>&1(1>&2) is too complicated to understand!

foo.sh
```

#!/bin/bash

echo "stdout"
echo "stderr" 1>&2
```

standard output(1) shows "stdout", and standard error(2) shows "stderr".

$ chmod +x foo.sh

I know how to make both 1 and 2 be the copy of /dev/null.

$ ./foo 1>/dev/null 2>&1 # valid command

But I try below command for test.
 
$ ./foo.sh 2>&1 1>/dev/null 2>err # invalid command


First Step(2>&1), 2>&1 means dup2(1,2). dup2 makes standard error(2) be the copy of standard output(1).

1 => screen
2 => screen

Second Step(1>/dev/null), it means dup2(/dev/null,1), which makes standard output be the copy of /dev/null.

1 => /dev/null
2 => screen

Then, I add 2>err. I think no characters on screen. Because

1 => /dev/null
2 => err

But screen shows "stderr" and "stderr" in file err. Why?

In another test, 

$ ./foo.sh 1>&2 1>std
stdout
stderr
$ cat stdout

why ?

---

### Post by dave01945 on 2011-09-30
i'm not totally sure what you are asking but 2>&1 redirects stderr to stdout and 1>&2 redirects stdout to stderr both are usually displayed onscreen but in a script stdout can but set to a variable but stderr can't unless you redirect stderr to stdout (2>&1)

---

