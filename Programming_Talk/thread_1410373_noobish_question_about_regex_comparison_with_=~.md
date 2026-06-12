---
title: "noobish question about regex comparison with =~"
date: 2010-02-18
forum: Programming Talk
---

### Post by Elcid247 on 2010-02-18
i just can't get it to work and can't seem to see what i'm doing wrong.

```
#!/bin/sh

if [[ "$1" =~ "[a-zA-Z][a-zA-Z]$" ]]
then
	echo $1
fi
```


it keeps saying "[[: not found" for any regular expression and parameter i try :-S

i copied the if condition from [here]("http://tldp.org/LDP/abs/html/contributed-scripts.html#WHX")

can some1 test this or tell me if its working or whats wrong with it?

---

### Post by DaithiF on 2010-02-18
Hi, 2 things:
1. use #!/bin/bash rather than #!/bin/sh
2. as of bash 3.2 the matching expression should no longer be included in quotes, so
```
if [[ "$1" =~ [a-zA-Z][a-zA-Z]$ ]]
then
   echo $1
fi

```

---

### Post by Elcid247 on 2010-02-18
> **DaithiF said:**
> Hi, 2 things:
1. use #!/bin/bash rather than #!/bin/sh
2. as of bash 3.2 the matching expression should no longer be included in quotes, so
```
if [[ "$1" =~ [a-zA-Z][a-zA-Z]$ ]]
then
   echo $1
fi

```

:-S thanks a lot mate, never would've figured that out myself.


Thanks again.

---

