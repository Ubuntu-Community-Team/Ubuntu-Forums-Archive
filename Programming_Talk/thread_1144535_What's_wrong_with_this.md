---
title: "What's wrong with this?"
date: 2009-04-30
forum: Programming Talk
---

### Post by swoll1980 on 2009-04-30
```
#include <stdio.h>
#include <stdlib.h>

int main(void) {
  char *myenvvar=getenv("EDITOR");
  printf("The editor environment variable is set to %s\n",myenvvar);
}
```

I get a syntax error, it's bash

---

### Post by doas777 on 2009-04-30
disregard. it compiled fine for me, but did give a warning that it was reaching the end of main without getting an exit signal. I just added exit(0); to the end of the block to make it go away.

---

### Post by lisati on 2009-04-30
Compiles ok on my machine, and running the compiled file gives the following output:
> The editor environment variable is set to (null)

EDIT: It's bash? Looks like a "C" program to me. I put the code in a file temp.c, made sure that build-essential was installed. typed in ```
gcc temp.c -o temp
./temp

```

---

### Post by swoll1980 on 2009-04-30
> **lisati said:**
> Compiles ok on my machine, and running the compiled file gives the following output:


EDIT: It's bash? Looks like a "C" program to me. I put the code in a file temp.c, made sure that build-essential was installed. typed in ```
gcc temp.c -o temp
./temp

```

OK thanks. after I compiled I tried to run it 
```
./myenv.c 
```
I forgot to drop the .c thanks for the help. I'm just learning this stuff. Sorry for wasting your time.

---

### Post by lisati on 2009-04-30
> **swoll1980 said:**
> OK thanks. after I compiled I tried to run it 
```
./myenv.c 
```
I forgot to drop the .c thanks for the help. I'm just learning this stuff. Sorry for wasting your time.

No, it wasn't a waste of time. I'm still learning too.

EDIT: It could be worse: With MS-DOS we'd have the choice between a .COM and an .EXE file; when producing an .EXE file we'd have a choice of MS-DOS only, a MS-DOS box within Windows, or one that uses the Windows GUI.

---

### Post by sekinto on 2009-04-30
If that is C there should be a
```
return 0;
```
at the end of the main function.

---

