---
title: "how to pass arguments with space inside to bash script?"
date: 2009-04-09
forum: Programming Talk
---

### Post by flylehe on 2009-04-09
Hi,
I was wondering how to pass arguments with space inside. For example, my bash script looks like:
```

#!/bin/bash
ARG_OPTS=""
while [[ -n "$1" ]];
        ARG_OPTS="${ARG_OPTS} $1"
        shift
done

```
If I pass an argument like 
> 
--options='-t 0 -v 0'

then it would be splitted by the spaces inside, ie "--options='-t", "0", "-v" and "0".

Shall I change the format of argument, or change my bash script?

Thanks and regards!

---

### Post by andrewc6l on 2009-04-09
In the past, I've seen programs use:
 -option1 -option2 "-option3=-t 0 -v 0" -option4

This works in bash, but would obviously need a little parsing.

---

### Post by flylehe on 2009-04-09
Thanks!

Actually besides as argument to the bash script, > --options='-t 0 -v 0' is supposed to be further passed as an argument to an executable in the bash script as in this call to the executable:
> my_executable ${ARG_OPTS} .

Also I just found if I double quote it, i.e. 
> 
"--options='-t 0 -v 0'"

as argument to the bash script, then the '-t 0 -v 0'  as a whole can be preserved until reaching the command invoking the executable. 

However the '-t 0 -v 0' is not passed as a whole to the executable,  but splitted by spaces again. This may sounds like it is the problem of calling the executable, however when directly invoking the executable from terminal,> --options='-t 0 -v 0' could be passed successfully as argument. So can >  --options="-t 0 -v 0" 

Hope that I could explain my question clearly. Really appreciate your advice!

---

### Post by Cracauer on 2009-04-11
There is a getopt(1).

---

