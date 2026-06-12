---
title: "shell scripting problem"
date: 2007-01-20
forum: Programming Talk
---

### Post by jordilin on 2007-01-20
I've done a script to find out what users can't enter a server because they don't have a a defined shell looking at the /etc/passwd file. A user in this file has a line like this:
> jordilin:x:1000:1000:Jordi Carrillo,,,:/home/jordilin:/bin/bash

So anyone who does not have the /bin/bash at the end can't enter. I want the script to write down the name of the user. So If I didn't have the final /bin/bash it should write Jordi Carrillo.
the code is like follows
```
#!/bin/bash
USERS=$(awk -F : '{if ($3>=1000) print}' /etc/passwd)

for i in $USERS
do
        HASHELL=`echo $i | grep "bash"`
        if [ $HASHELL!="" ]
        then
                (pseudocode) write the user name
        fi
done

```
the main problem I have is that between my name Jordi and my surname Carrillo there's a blank space and it does not work.

---

### Post by supirman on 2007-01-20
You don't really need a script, just update your awk command a bit:


```
awk -F : '{if ($3>=1000 && $7!="/bin/bash") print $5}' /etc/passwd
```

---

### Post by jordilin on 2007-01-20
Oops, you are right, thanks indeed!!

---

