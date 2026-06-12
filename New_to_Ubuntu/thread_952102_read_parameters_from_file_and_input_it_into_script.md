---
title: "read parameters from file and input it into script"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by daniel3ub on 2008-10-18
Hi, pals.

I have a script that uses 3 parameters when called from the command line:

```

script01.sh parameter1 parameter2 parameter3

```

I need to write a second script to call this script01.sh a couple of times with diferent parameters, so I want to put this parameters in a file params.txt, something like this:

```

file params.txt:
param1 param2 param3
param1 param2 param3
param1 param2 param3

```

Note that the params can be quoted, like "this parameter", so I cannot use spaces as separators.

Is there a simple way of doing this? I've been searching the net for a few days and every possible solution seems a lot complicated for a guy that is starting with shell scripting like me.

Is there a way of doing this without using sed, for example? (I can never understand sed syntax...)

Thanks a lot!

---

### Post by RealPSL on 2008-10-18
I am not 100% sure I understand so I can going to provide you 2 options. One in which the separator is a ":" and one with a space. 

```
#!/bin/bash

while read param1 param2 param3
do
        echo "$param1 $param2 $param3"
done
```

The above will read input from a file like below and just print it back to screen.

> "This is 1" "This is 2" 3

In this second example we use ":" as the separator. Here is the code
```
#!/bin/bash

while read line
do
        param1=`echo $line | cut -d: -f1`
        param2=`echo $line | cut -d: -f2`
        param3=`echo $line | cut -d: -f3`
        echo "$param1 $param2 $param3"
done

```

Here is the file:

> This is 1:This is 2:3

---

