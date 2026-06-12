---
title: "[SOLVED] bash problem. syntax error?"
date: 2008-07-19
forum: Programming Talk
---

### Post by spacesearcher on 2008-07-19
ok so i am trying to learn to write bash scripts. I found this page that is helping: [http://www.ibm.com/developerworks/library/l-bash2.html](http://www.ibm.com/developerworks/library/l-bash2.html)
im trying to do the String comparison caveats section. so i write this script
```

#!/bin/bash

if [ "$myvar" = "foo bar oni" ]
then
    echo "yes"
fi

```
 then save it as myscript.sh
in terminal i cd to the directory and do:
```

joe@joe-laptop:~/Computer practice$ chmod 755 myscript.sh
joe@joe-laptop:~/Computer practice$ myvar="foo bar oni"
joe@joe-laptop:~/Computer practice$ ./myscript.sh
joe@joe-laptop:~/Computer practice$ echo $myvar
foo bar oni
joe@joe-laptop:~/Computer practice$ 

```
it never echos yes like it should. >.< this is driving me crazy. all examples have worked but this one hasn't. Am I just not understanding something?

---

### Post by ghostdog74 on 2008-07-19
use case
```

case "$myvar" in 
 "foo bar oni" ) echo "yes";;
 * ) echo "no";;
esac

```

---

### Post by spacesearcher on 2008-07-19
thank you!
I think I will have a good look at the link in  your sig to bash scripting. it seems like more what im after.

---

### Post by WW on 2008-07-19
You need to **export** the variable for it to be visible in the script, or execute the script using the bash builtin command **source** (or define the variable in the script itself).  Here is myscript.sh with an extra echo statement:

myscript.sh
```

#!/bin/bash
echo "myvar is '$myvar'"
if [ "$myvar" = "foo bar oni" ]
then
    echo "yes"
fi

```

Here it is in use:
```

$ ./myscript.sh
myvar is ''
$ myvar="foo bar oni"
$ ./myscript.sh
myvar is ''
$ source myscript.sh 
myvar is 'foo bar oni'
yes
$ export myvar
$ ./myscript.sh
myvar is 'foo bar oni'
yes
$ 

```

---

