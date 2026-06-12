---
title: "How to save terminal output?"
date: 2012-05-30
forum: Programming Talk
---

### Post by chepe263 on 2012-05-30
I would like to save the terminal output to a temporary variable.

For example, if i execute a command to start lampp I would like to save the contents and show them with  notify-send.

I have read this

[http://www.unix.com/unix-advanced-expert-users/51286-terminal-output-file.html](http://www.unix.com/unix-advanced-expert-users/51286-terminal-output-file.html)

but i have no idea how to save it to a variable and then display it with notify-send command.

---

### Post by lykwydchykyn on 2012-05-30
Try:
```

MYVARIABLE=$(mycommands)

```

Note the lack of spaces around the =.  This is important.

---

### Post by chepe263 on 2012-05-30
> **lykwydchykyn said:**
> Try:
```

MYVARIABLE=$(mycommands)

```

Note the lack of spaces around the =.  This is important.


Entonces,

> myvar=$(sudo lampp start) && notify-send $myvar

will be ok?

---

### Post by codemaniac on 2012-05-30
Nothing wrong in using $myvar recursively in your example .
Give it a try .

---

### Post by chepe263 on 2012-05-30
> **codemaniac said:**
> Nothing wrong in using $myvar recursively in your example .
Give it a try .

works but it's better

> myvar=$(sudo lampp start) && notify-send "$myvar"

Now, how do i turn it into a bash script?

---

### Post by zombifier25 on 2012-05-30
Like this:
```

#!/bin/bash
myvar=$(sudo lampp start) && notify-send "$myvar" 

```
And save it as something.sh. After that, make it executable:
```
chmod +x something.sh
```
You can put it in your ~/bin directory so that you don't have to type /link/to/something.sh, just something.sh

---

### Post by chepe263 on 2012-05-30
> **zombifier25 said:**
> Like this:
```

#!/bin/bash
myvar=$(sudo lampp start) && notify-send "$myvar" 

```
And save it as something.sh. After that, make it executable:
```
chmod +x something.sh
```
You can put it in your ~/bin directory so that you don't have to type /link/to/something.sh, just something.sh

What about passing parameters to it? What about having a deffault paramenter of use one provided?

---

### Post by codemaniac on 2012-05-30
> **chepe263 said:**
> What about passing parameters to it? What about having a deffault paramenter of use one provided?

You can always pass parameters to your script .
Something like below .
Please note that the code is not tested .
Just trying to give you an idea to get started . 
```

#!/bin/bash

for option in $*
do
        case $option in
        -m) shift
            myvar=$1
            
            shift
        ;;
        -s) shift
           server=$1
            
            shift
        ;;
        -*) echo "Invalid Option"
        ;;
        esac

done

myvar=$(sudo $server start) && notify-send "$myvar"

```

---

