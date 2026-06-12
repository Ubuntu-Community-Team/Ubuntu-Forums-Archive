---
title: "Need help for a bash script ( arg -exec in find)"
date: 2007-01-02
forum: Programming Talk
---

### Post by mallo on 2007-01-02
Hi everybody,
I have a problem in one of my shell scripts.

When I execute it the shell gives this message:
find: missing argument to `-exec'

I summarized the script work:

#!/bin/bash

ARGSEXEC=" -exec du -s --apparent-size --block-size=1 '{}' \;| awk '{if($(echo '$1')>1000)print}' | sed -e 's/^[0-9,M,K]*\t//g'";	

echo "other lines..."

TYPE="-type d"

echo "other lines..."

echo " Try the cut and paste with this: "
echo $TYPE $ARGSEXEC

echo "And now : "
find ~ $TYPE $ARGSEXEC


##########END#########

The issue is resolved if I run the output echo cutting and pasting it in a new line with:
find ~ here-I-paste

Obviously the script is intended to run without this stratagem :P.
And i cannot write 
find ~ -type d -exec $VAR
because all the strings are the result of some functions.

Anybody can guess a solution?

More, I need some advice about how to modifying it for --block-size=M or K;
In that case I cannot use a simple $1 > number because $1 is of that sort numberM or numberK. I'd need some sort of cut of the last char only if is between a-Z [or excluding 0-9].


Thanks a lot for anybody who will try :)

---

### Post by duff on 2007-01-02
haven't tried it yet, but what if you put "eval" before your find statement (eval find ~ yada...)

---

### Post by mallo on 2007-01-03
:-D 
It works, simple yet effective. I like it ^_^.

Now I'll work on K, M problem.

Thanks a lot!

---

### Post by mallo on 2007-01-03
I tested some variants.

Why this line does not work?

find ~ -type d -exec du -s --apparent-size --block-size=M '{}' \;| awk '{temp=(( echo $1 | sed -e 's/[K-M]//g' ));print temp}'


I want to delete the M, K character in $1....then I'll apply the idea to the previous script and use temp variable in if... 

Anybody can help me? Do you think is a good idea?

---

### Post by mallo on 2007-01-03
Never mind, I'll try another solution, simpler I think :)

[I'll mantain byte and use a form like: if($1 > 10*$VAR)] where VAR is 1024 for K or 1024*1024 for M...]

---

