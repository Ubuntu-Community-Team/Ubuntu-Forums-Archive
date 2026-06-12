---
title: "problem with shell script"
date: 2011-05-09
forum: Programming Talk
---

### Post by Mia_tech on 2011-05-09
guys I have this simple script that it works when I remove the function, but when I use it with the function it always gives me "Error: missing args" even though I'm passing args. I'm calling script like: ./mydirs newdir
here's the code

```
#!/bin/bash

mydir() {
if [ $# -lt 1 ]; then
        echo "Error: missing args"
        exit 1
fi

mkdir $1 > /dev/null 2>&1
if [ $? -eq 0 ]; then
        cd $1 > /dev/null 2>&1
        if [ $? -eq 0 ]; then
                echo $PWD
        else
                echo "Error changing directories"
        fi
else
        echo "Error unable to make directory"
fi
}

mydir

```

---

### Post by dwhitney67 on 2011-05-09
When you call the function, pass the args that were given to the script.  For example:
```

...

mydir $*   # or just pass $1

```

As for code etiquette, you should consider using some indentation for the code within the function so that it stands out better.  Also, do not bury too much functionality within a function; keep it simple.  Your sole function is attempting to make a directory AND change to the directory.

P.S.  Your code would fail if someone passed as a command line arg the following:  "newdir/subdir".  Use the -p option with mkdir.

---

### Post by Mia_tech on 2011-05-09
yeah, passing parameters in function call was the problem...

---

### Post by hakermania on 2011-05-09
Nice solution!
I'll use it in the future!

---

