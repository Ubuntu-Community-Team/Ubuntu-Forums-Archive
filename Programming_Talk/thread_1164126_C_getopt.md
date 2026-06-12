---
title: "C getopt"
date: 2009-05-19
forum: Programming Talk
---

### Post by matmatmat on 2009-05-19
I'm trying to make a simple todo list program/thingy, I am using getopt to recognise options (eg '-a hello' where hello is the option (optarg?):
```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main(int argc, char *argv[]){
        FILE *f;
        int optchar;
        while (optchar = getopt(argc, argv, "a:") != -1){
                switch (optchar){
                        case 'a':
                                printf(optarg);
                                printf("case 'a'\n");
                                break;
                        
                }
                if (optchar == "a"){
                        printf("if \"a\"");

               }
               if (optchar == 'a'){
                        printf("if 'a'");
               }
       }
}

```
when run nothing is outputted?

---

### Post by iiska on 2009-05-19
While condition gets evaluated in wrong order and value 1 is stored to optchar always. Try to add a couple parenthesis to it like this:

```

while ( (optchar = getopt(argc, argv, "a:")) != -1){

```

---

### Post by matmatmat on 2009-05-19
Thanks

---

