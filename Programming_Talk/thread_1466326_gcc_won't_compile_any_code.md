---
title: "gcc won't compile any code"
date: 2010-04-30
forum: Programming Talk
---

### Post by Vichfret on 2010-04-30
When I try to compile it get there errors:

[http://pastebin.com/RmfwPEcH](http://pastebin.com/RmfwPEcH) I already installed build-essential, what could be happening with my gcc compiler?

btw it's not solved... I'm sleepy and I checked the thread as solved...

---

### Post by MadCow108 on 2010-04-30
please also show the source code not only the errors

check if there is a stddef.h somewhere in your /usr/include folder

---

### Post by Vichfret on 2010-04-30
```
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char *argv[]) {
    int i;
    char *comando, **argumentos;

    comando = (char *)malloc(sizeof(char)*5);
    argumentos = (char **)malloc(sizeof(char *)*3);
    argumentos[0] = (char *)malloc(sizeof(char)*3);
    argumentos[1] = (char *)malloc(sizeof(char)*4);
    argumentos[2] = (char *)malloc(sizeof(char)*50);

    strcpy(comando, "ping");
    strcpy(argumentos[0], "-c");
    scanf("%s", argumentos[1]);
    scanf("%s", argumentos[2]);
    execv(comando, argumentos);

    for(i=0; i<3; i++)
        free(argumentos[i]);
    free(argumentos);
    free(comando);
}
```and

```
#include <stdio.h>
#include <stdlib.h>

int main() {
    int i;
    /*char *comando, **argumentos;

    comando = (char *)malloc(sizeof(char)*5);
    argumentos = (char **)malloc(sizeof(char *)*3);
    argumentos[0] = (char *)malloc(sizeof(char)*3);
    argumentos[1] = (char *)malloc(sizeof(char)*4);
    argumentos[2] = (char *)malloc(sizeof(char)*50);

    strcpy(comando, "ping");
    strcpy(argumentos[0], "-c");
    scanf("%s", argumentos[1]);
    scanf("%s", argumentos[2]);
    execv(comando, argumentos);

    for(i=0; i<3; i++)
        free(argumentos[i]);
    free(argumentos);
    free(comando);*/
    scanf("%d",&i);
    printf("%d", i);
}
``````
vicfred@Elain ~/src/c % locate stddef.h                                                                                <11:55>
/usr/include/linux/stddef.h
/usr/lib/gcc/i486-linux-gnu/4.4/include/stddef.h
```

---

### Post by dwhitney67 on 2010-04-30
The first program you posted is missing the following:
```

#include <string.h>   /* for strcpy */
#include <unistd.h>   /* for execv */

```

Both programs compile fine on my system, using the 'gcc' command.

Please indicate how you are compiling your programs, and also explain why stddef.h is relevant in this discussion.  You do not appear to include it anywhere.  Is it perhaps included by one of the header files that you have specified?

---

### Post by MadCow108 on 2010-04-30
compile with an additional -v flag

this should output something similar to this:
...
#include <...> search starts here:
/usr/local/include
/usr/lib/gcc/i486-linux-gnu/4.4.3/include
/usr/lib/gcc/i486-linux-gnu/4.4.3/include-fixed
/usr/include
...

the folder containing the stddef file should be in that list
I'm a little surprised that your stddef is in the 4.4 folder and not in the 4.4.X folder
on my system there are only object files in the 4.4 folder
the headers are in the 4.4.X folder

---

### Post by Vichfret on 2010-04-30
I'm compiling my code with gcc. I added the libraries string and unistd and now compiling with:

```
gcc -v execv.c -o hola
```

I get this: 

[http://pastebin.com/dLYFzyL6](http://pastebin.com/dLYFzyL6) and stddef is important because gcc is not finding it when I include stdio/stdlib (the log for that is in the first post)

---

### Post by MadCow108 on 2010-04-30
how have you installed gcc?
which operating system are you using?
you are using a svn snapshot of gcc. maybe the problem lies in that.

a workaround would be to compile with this:
-I/usr/lib/gcc/i486-linux-gnu/4.4/include/

---

### Post by Vichfret on 2010-04-30
yes I installed it, I'm using Debian squeeze

---

### Post by lisati on 2010-05-01
@Vichfret: you don't need [noparse]```
 and 
```[/noparse] around links to another page: the forum software will automatically do the stuff to let people click on the links and see what you're quoting. Putting [noparse]```
 and 
```[/noparse] around code is OK.

---

### Post by Vichfret on 2010-05-02
I already solved the problem, I found that Debian does not support to change my $PATH to something like this:

```
/usr/local/lib/cw:/usr/local/bin:/usr/bin:/bin:/usr/bin/X11:/usr/game
```

cw is a colour wrapper for the terminal.

Now gcc work with my path like this: 

```
/usr/local/bin:/usr/bin:/bin:/usr/bin/X11:/usr/game:/usr/local/lib/cw
```

but cw is not working, I guess I can live without colours in my terminal...  :(

---

