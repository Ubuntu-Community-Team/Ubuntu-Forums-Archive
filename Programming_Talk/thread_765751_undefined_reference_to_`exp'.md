---
title: "undefined reference to `exp'"
date: 2008-04-24
forum: Programming Talk
---

### Post by jsmidt on 2008-04-24
I can't get the below code to compile.  I am trying to call the exp() function in C.  I have included math.h, so I don't know what the problem is.

Any help would be appreciated.  Here is the code:

```
#include <stdio.h>
#include <math.h>

int main()
{
    int i;

    for(i=1;i<3;i++){
        printf("Exp(i) = %f \n\n", exp(i));
    }

    return 0;
}
```


Here is the error:

```
main.c:(.text+0x21): undefined reference to `exp'
```

---

### Post by LaRoza on 2008-04-24
use this to compile:

```

gcc main.c -lm 

```

(and whatever flags you use, just add the -lm)

---

### Post by jsmidt on 2008-04-24
Thanks, that worked.

Just a question.  Why did I have to do that?  Why does -lm make it work?

---

### Post by LaRoza on 2008-04-24
> **jsmidt said:**
> Thanks, that worked.

Just a question.  Why did I have to do that?  Why does -lm make it work?

It links to the math library, which is a standard library, but has to be manually linked (the only C standard library to require this)

Why does it have to be done? I am really not sure.

---

### Post by lnostdal on 2008-04-24
if you type *man exp* you'll see they mention "Link with -lm" there.

The reason? I'm not sure to be honest. I guess they want to keep some of the less commonly used code outside of glibc to save space. (-lm tells the linker to link with /usr/lib/libm.so)

edit:
you beat me to it, LaRoza ... =)

---

### Post by Lux Perpetua on 2008-04-24
As far as I know, it's a holdover from a time in which computational resources were more precious. I guess the system is still valid today inasmuch as those resources (mainly compilation time, I would think) are still precious.

---

