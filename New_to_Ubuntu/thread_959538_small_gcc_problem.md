---
title: "small gcc problem"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by francisc1701 on 2008-10-26
hello!

I wrote a small program in C, I included math.h (#include <math.h>), but when I compiled with ```
gcc -o test test.c
``` I got the following error: ```
undefined reference to `sqrt'
```
Yesterday I found a solution to this in the form of a command line switch for gcc that tells it to look for math.h. For one thing I don't remember what that switch was :( or where I found it - google found it for me.
Another thing: is there some conf file for gcc where I could tell it to look for math.h, so I don't have to use that switch every time I compile something?

Thanks in advance

---

### Post by Xiong Chiamiov on 2008-10-26
It's [the -lm flag]("http://www.linuxforums.org/forum/linux-programming-scripting/119589-undefined-reference-sqrt.html").  You can probably set up an alias in your ~/.bashrc with something like this:
```

alias gcc='gcc -lm'

```
This will only work on new shells.  I'd recommend typing that in your shell prompt first to see if it works.

---

### Post by francisc1701 on 2008-10-26
> **Xiong Chiamiov said:**
> It's [the -lm flag]("http://www.linuxforums.org/forum/linux-programming-scripting/119589-undefined-reference-sqrt.html"). Yes indeed it is. Thanks.

> **Xiong Chiamiov said:**
> You can probably set up an alias in your ~/.bashrc with something like this:
```

alias gcc='gcc -lm'

```
This will only work on new shells.  I'd recommend typing that in your shell prompt first to see if it works.
So every time I type "gcc" in a konsole it will be replaced with "gcc -lm"? What happens if I create such an alias and I also add the switch to gcc? (I'd have to be dim to do that, but still)

---

### Post by dracayr on 2008-10-26
It would be the same as using gcc -lm -lm, which I guess works fine (try it, if you want to be sure)

dracayr

---

### Post by Xiong Chiamiov on 2008-10-26
> **francisc1701 said:**
> 
So every time I type "gcc" in a konsole it will be replaced with "gcc -lm"? What happens if I create such an alias and I also add the switch to gcc? (I'd have to be dim to do that, but still)

Yes, that is correct.  I don't think adding the same flag twice would have any ill effects, although testing is the only way to find out if gcc complains about it.

---

### Post by francisc1701 on 2008-10-26
gcc didn't complain.

thanks

---

