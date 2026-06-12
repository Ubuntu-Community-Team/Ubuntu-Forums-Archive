---
title: "printf problem"
date: 2008-02-21
forum: Programming Talk
---

### Post by cacaegg on 2008-02-21
hello, I want to learn C in ubuntu env, but I got a problem as I just start to print out "hello world" program. I want to use printf to show some message, but it didn't show on the terminal(I use pietty to remote log on the ubuntu), is there any help?

#include<stdio.h>
#include<stdlib.h>

int main (int argc, char* argv[]){
        printf("hello");
        return 0;
}

---

### Post by foo-bar on 2008-02-21
if thats all the code you have, and you are not seeing any output, try putting:

```

fflush(stdout);

```

after your printf.

---

### Post by lnostdal on 2008-02-22
it works here, but it's kinda hard to see the "hello" .. 

```

lars@ibmr52:~/programming/c$ gcc -Wall -g -o a a.c
lars@ibmr52:~/programming/c$ ./a
hellolars@ibmr52:~/programming/c$ 

```

if you add a newline it is easier to see:

```

lars@ibmr52:~/programming/c$ cat a.c
#include <stdio.h>
#include <stdlib.h>

int main (int argc, char* argv[]){
  printf("hello\n");
  return 0;
}

lars@ibmr52:~/programming/c$ gcc -Wall -g -o a a.c
lars@ibmr52:~/programming/c$ ./a
hello
lars@ibmr52:~/programming/c$ 

```

---

