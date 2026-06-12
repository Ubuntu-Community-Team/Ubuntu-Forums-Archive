---
title: "moving variables from script to script"
date: 2013-03-12
forum: Programming Talk
---

### Post by cbillson on 2013-03-12
as an example if i call setup1.sh and declare:

a=1
b=2

then launch setup2.sh

a=
b=


is there any way i can carry variables from one script when i call another within it?

Cheers
Chris
[INDENT][/INDENT]
[INDENT][/INDENT]

---

### Post by The Cog on 2013-03-12
export a=1
export b=2
setup2.sh

---

### Post by cbillson on 2013-03-12
is there any way to take all variables (or current environment) - or is it purely a var by var basis?

---

### Post by schragge on 2013-03-12
> **cbillson said:**
> current environment```
[env]("http://manpages.ubuntu.com/manpages/precise/en/man1/env.1.html") setup2.sh
```
Obviously, this won't work for variables defined in another script, but not exported to the environment.

---

### Post by Habitual on 2013-03-12
source setup1.sh in setup2.sh?

---

### Post by cbillson on 2013-03-13
Clearly i'm misunderstanding what has been suggested :(
[INDENT]admin@server1:logs$ cat script1.sh
a=1
b=2
c=3
env ./script2.sh

admin@server1:logs$ sudo cat script2.sh
echo a $a
echo b $b
echo c $c
admin@server1:logs$ sudo ./script1.sh
a
b
c
[/INDENT]

---

### Post by schragge on 2013-03-13
I'd rather define the variables in another file say *common_env.sh*, and source it from both your scripts as Habitual suggested:
```

[COLOR=green]$[/COLOR] cat common_env.sh
[COLOR=green]a=1 b=2 c=3[/COLOR]
```
```

[COLOR=green]$[/COLOR] cat script1.sh
[COLOR=green]#!/bin/sh
. ${0%/*}/common_env.sh
echo $0: $a $b $c
[/COLOR]
```
```

[COLOR=green]$[/COLOR] cat script2.sh
[COLOR=green]#!/bin/sh
. ${0%/*}/common_env.sh
echo $0: $a $b $c
[/COLOR]
```
```

[COLOR=green]$[/COLOR] ./script1.sh
[COLOR=green]./script1.sh: 1 2 3[/COLOR] 
[COLOR=green]$[/COLOR] ./script2.sh
[COLOR=green]./script2.sh: 1 2 3[/COLOR] 

```

---

### Post by prodigy_ on 2013-03-13
Or you can store vars in a text file and **source** them from there: ```

#!/bin/sh

varSave () {
	# Appends variable $1 to file $2.
	printf "%b\n" "$1=\"$(eval printf "%s" \"\$$1\")\""  >> $2
}

a=1
b=2
c=3

for i in a b c; do
	varSave $i ./vars
done

```

Yeah, this function IS ugly. :) But it works. Now in the second script you only need **source ./vars**.

---

### Post by schragge on 2013-03-13
@**prodigy_**
The function can be somewhat simplified by using bash-specific syntax for indirect parameter reference:
```

#!/bin/bash
varSave () {
    printf '%s\n' "$1='${!1}'" >> $2
}

```

---

