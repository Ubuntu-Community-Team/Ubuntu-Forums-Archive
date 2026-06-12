---
title: "[bash] Handling special characters in filenames."
date: 2010-07-26
forum: Programming Talk
---

### Post by prodigy_ on 2010-07-26
First of all, I know the theory (**find ... -exec ... **, **find ... print0 | xargs -0 ... **, etc). But nothing seems to work if I need to pipe the output because not all commands support ASCII NUL character as a delimiter. And even with those that support NUL, it's not always possible to use it. For example, **file -0 ... |grep -z ...** technically works but fails to produce a meaningful output.

To illustrate the problem, let's imagine that we want to remove all JPEG files from **/example** directory. The best method I can come up with would be:

```
find /example -type f -print0|xargs -0 file -F '/' \
        |grep 'JPEG'|rev|cut -d '/' -f 2-|rev \
        |tr '\012' '\000'|xargs -0 rm
```

But obviously this wouldn't properly handle filenames with newline characters in them.

Therefore, a question: is there a better way? Is it possible to handle all allowed characters (which means all characters except slash and NUL) and use pipelines at the same time?

P.S. The example I used is just for clarification. If possible, I'm looking for a universal method applicable to all situations.

---

### Post by ghostdog74 on 2010-07-26
```

find /example -type f -iname "*.JPEG" -print0 | while read -r -d $'\0' FILE
do
  ....
done

```

---

### Post by prodigy_ on 2010-07-27
You see, the problem is that **within** the cycle, any command that doesn't have an option to substitute NULs for line breaks will ruin all the effort.

For example, **file -0** uses NULs to separate file names from the rest of the output. Seems fine so far? Yes. It's even mentioned in the man page that you should be able to filter everything else out with **cut**. But **file -0** doesn't substitute NULs for its own line breaks:
```

#!/bin/bash

find /example -type f -print0| \
while read -r -d $'\0' FILE
do
        file -0 $FILE|od -c
done

<---snip--->

$bash test.sh
0000000   /   e   x   a   m   p   l   e   /   e   m   b   l   e   m   -
0000020   n   e   w   .   i   c   o   n  \0       U   T   F   -   8    
0000040   U   n   i   c   o   d   e       t   e   x   t  \n
0000055
0000000   /   e   x   a   m   p   l   e   /   e   m   b   l   e   m   -
0000020   p   r   e   s   e   n   t   a   t   i   o   n   .   s   v   g
0000040  \0       S   V   G       S   c   a   l   a   b   l   e       V
0000060   e   c   t   o   r       G   r   a   p   h   i   c   s       i
0000100   m   a   g   e  \n
0000105
0000000   /   e   x   a   m   p   l   e   /   e   m   b   l   e   m   -
0000020   d   e   v   e   l   o   p   m   e   n   t   .   i   c   o   n
0000040  \0       U   T   F   -   8       U   n   i   c   o   d   e    
0000060   t   e   x   t  \n
0000065
0000000   /   e   x   a   m   p   l   e   /   e   m   b   l   e   m   -
0000020   c   o   o   l   .   i   c   o   n  \0       U   T   F   -   8
0000040       U   n   i   c   o   d   e       t   e   x   t  \n

<---snip--->

```

Since newlines are permitted in filenames, technically we're screwed already. Similarly, **cut -d $'\0' --outpit-delimiter $'\0'** still uses LFs for line breaks.

---

After reading [this](http://www.dwheeler.com/essays/fixing-unix-linux-filenames.html), I'm pessimistic. Seems there's no easy way...

---

