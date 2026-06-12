---
title: "[SOLVED] sending an indefinite number of arguments to a shell script?"
date: 2008-09-03
forum: Programming Talk
---

### Post by blakecraw on 2008-09-03
The various times I've written small shell scripts, I haven't bothered to find this out, but how do I write a script so that it can accept however many arguments I decide to send it?

What I have so far is:

[php]
for i in `seq "$#"` ; do
[/php]

but then how do I do something to each argument (the same thing to each argument)?

---

### Post by ghostdog74 on 2008-09-03
> **blakecraw said:**
> The various times I've written small shell scripts, I haven't bothered to find this out, but how do I write a script so that it can accept however many arguments I decide to send it?

What I have so far is:

[php]
for i in `seq "$#"` ; do
[/php]

but then how do I do something to each argument (the same thing to each argument)?
```

#!/bin/bash
for arg in $@
do
    echo $arg
done 


```
```

for arg in `seq $#`
do
    eval echo \${$arg}
done 

```
check my sig for learning bash.

---

### Post by blakecraw on 2008-09-04
thanks a lot ghostdog, just what I was looking for. And I will certainly check out the guides in your sig.

---

