---
title: "How to get primary group only?"
date: 2010-07-27
forum: Programming Talk
---

### Post by emtapcode on 2010-07-27
Hi everyone. I'm newbie at Ubuntu.
I have a question, can you help me answer:
How is the easiest way to echo ONLY primary group (initial group) from user which I typed?

Thanks in advance,
Regards.,

---

### Post by viralmeme on 2010-07-27
> **emtapcode said:**
> How is the easiest way to echo ONLY primary group (initial group) from user which I typed?

$id -gn

---

### Post by emtapcode on 2010-07-27
> **viralmeme said:**
> $id -gn

Wow, thank you very much. I think this is the shortest way :p
Thanks again.

---

### Post by emtapcode on 2010-07-28
And anyone can help me How to echo supplementary groups ONLY?
Because when I use: $id -Gn ,this command displays initial group and supplementary groups.
Many thanks :)

---

### Post by dwhitney67 on 2010-07-29
Here's a couple of ways:
```

id -Gn | awk '{for(i=2; i<=NF; i++) printf("%s ",$i); print ""}'

id -Gn | cut -d" " -f2-

```
I'm sure there's an easier way.  I'm not a bash expert.

---

### Post by ghostdog74 on 2010-07-29
you can use bash

```

$ declare -a var
$ var=($(id -Gn))
$ echo ${var[@]:2}

```

---

### Post by emtapcode on 2010-07-29
@dwhitney67: thanks for your help. However, if my user be owned more two or more supplementary groups, your ways only display only the first supplementary groups.
@ghostdog74: thank you. But my result when i run this scripts are: 
Add a new user:
```
useradd -g gc -G gp,gc1 takana
```
```
#!/bin/bash

read n
`declare -a var`
var=($(id -Gn $n))
echo ${var[@]:2}

```

and my result:
```
gc1
```

But the correct answer is: gp and gc1

---

### Post by ghostdog74 on 2010-07-29
then adjust the index. Also there is no need to use backquotes

```

declare -a var
....
echo ${var[@]:1}

```

---

### Post by dwhitney67 on 2010-07-29
> **emtapcode said:**
> @dwhitney67: thanks for your help. However, if my user be owned more two or more supplementary groups, your ways only display only the first supplementary groups.

> 
And anyone can help me How to echo supplementary groups ONLY?
Because when I use: $id -Gn ,this command displays initial group and supplementary groups.

Say for example, if running 'id -Gn', generates the following output:
```

initGroup supGroupA supGroupB supGroupC

```
Using the examples I posted earlier, the initial group is removed from the result's list.  It seems from GhostDog74's second post, that his approach does the same.

What is it that you require?  Please be specific, because the terms "initial" and "supplementary", as used to describe groups, is not common parlance.  Well, at least not in my domain.

---

### Post by emtapcode on 2010-07-29
Thank you very much. I solved my problem. Thanks again and have a nice day :)

---

