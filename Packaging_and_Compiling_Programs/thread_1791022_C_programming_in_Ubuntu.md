---
title: "C programming in Ubuntu"
date: 2011-06-26
forum: Packaging and Compiling Programs
---

### Post by urihsur_navap on 2011-06-26
Hi,

i want to compile and run a simple hello world prgm.

```

#include <stdio.h>

int
main(int argc, char **argv){
        printf("hello world\n");
        return 0;
}
```

i compiled it using
```
gcc -o hello hello.c
```

but when i try to run it using 
```
. hello
```

i get an error ```
bash: .: hello: cannot execute binary file
```

what am i missing?? plz help.

also on the solaris machines at uni, to run a program you don't have to start with '.'. ie: to run hello, you would just type hello. how do u get this work in ubuntu?

thnx,

---

### Post by urihsur_navap on 2011-06-26
ahh figured it out. you need to type ```
./hello
``` to run it.

but still, in solaris all you need to type is the program name to run. any ideas how to do that in ubuntu?

thnx

---

### Post by sanderj on 2011-06-26
> **urihsur_navap said:**
> ahh figured it out. you need to type ```
./hello
``` to run it.

but still, in solaris all you need to type is the program name to run. any ideas how to do that in ubuntu?

thnx

To achieve that, you should add 'current directory' to your PATH. Google how to do that.

My advice: don't do it. You'll get used to typing "./hello". I do it all the time.

---

