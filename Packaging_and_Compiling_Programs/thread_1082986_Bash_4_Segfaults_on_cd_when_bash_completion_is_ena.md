---
title: "Bash 4 Segfaults on cd when bash completion is enabled"
date: 2009-02-28
forum: Packaging and Compiling Programs
---

### Post by Lieter on 2009-02-28
Hi all,

I compiled bash 4.0.0 from source with ```
./configure --prefix=/opt/
```

Now bash works fine when run as 
```
/opt/bin/bash --norc --noprofile
```

It however crashed when cd'ing when ran as 
```
/opt/bin/bash
```

as such:
```

lieter $ /opt/bin/bash --noprofile --rcfile .bashrc4 #this file contains only the lines from the next codeblock
bash-4.0$ cd workspace
bash-4.0$ pwd
/home/lieter/workspace
bash-4.0$ cd ..
bash-4.0$ cd workspace
Killed # I ran a kill -9 on the process since it sucked up 100% of one cpu core
```


After some debugging i traced it to the following lines in the .bashrc
```
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

```

The strange thing is:
when I completely type the directory name it does not crash, but when I use tab to complete the name it does. But when no rc is loaded it doesn't crash on a tab completed directory name. :confused:

I would want to know if anyone can reproduce this problem. I have a strace here i'll debug later, i first want to know what your initial reaction to this is.

---

### Post by Dorentus on 2009-03-09
Hi,
I'm using Debian sid+experimental.
Several days ago, I upgraded bash to 4.0(it's in experimental), and experienced the same problem.

Disabling bash completion could help, but I can't live without it.
So at last I downgraded bash to 3.2-5 and everything's back to normal.

---

### Post by peng2cheng2 on 2009-04-10
Thank you Leiter,

I just commented out the following in code my .bashrc, and file name completion works fine after cd in bash4.

if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

pc

---

