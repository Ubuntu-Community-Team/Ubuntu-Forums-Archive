---
title: "C strtok segfault in while-loop"
date: 2012-11-21
forum: Programming Talk
---

### Post by NixForFree on 2012-11-21
I got a strange behaviour of **strtok** in a simple c-programm: depending on where I put the line ptr=strok(NULL,",")  for subsequent calls, I get a segmentation fault error.

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main (void){
    FILE *f;
    char *p, temp[255];

    f=fopen("/home/user/file.csv","r");
    fgets(temp,255,f);  /* temp contains "12.23.34, 10, 22, 34, 45, 118, 337" now */

    p=strtok(temp,",");  
  [COLOR=Green] /* POSITION A: p=strtok(NULL,",") would correctly jump to the second element */[/COLOR]

   while(p!=NULL){
   [COLOR=Red] /* POSITON B: p=strtok(NULL,",") would produce a segfault here!!! */[/COLOR]
    printf("%d ",atoi(p));
    [COLOR=Green]p=strtok(NULL,","); /* this works fine again */[/COLOR]
    }
return EXIT_SUCCESS;
}
```Anyone an idea why?

---

### Post by Bachstelze on 2012-11-21
strtok() is a strange function, avoid it at all costs. Why not use sscanf()?

---

### Post by dwhitney67 on 2012-11-21
> **NixForFree said:**
> ```

    /* POSITON B: p=strtok(NULL,",") would produce a segfault here!!! */
    printf("%d ",atoi(p));

```Anyone an idea why?

I'm placing my wager that the line of code above is the culprit for the segfault.  You should be checking the value of 'p' _before_ passing it to atoi().

Otherwise, your code looks fine.

P.S.  For the fgets(), pass sizeof(temp), in lieu of 255, for the second parameter.

---

### Post by NixForFree on 2012-11-21
> **dwhitney67 said:**
> I'm placing my wager that the line of code above is the culprit for the segfault.  You should be checking the value of 'p' _before_ passing it to atoi().

Otherwise, your code looks fine.

P.S.  For the fgets(), pass sizeof(temp), in lieu of 255, for the second parameter.

Thanks for your reply. Of course you're right: your suggestions are better programming practice and eventually I'd change that, too. 
 
The problem, however, is definitely the first strok with NULL as an argument, which causes a segfault ONLY within the while-loop unless you "touche" the pointer by reading from it **first**. If I take the printf() line away the segfault is still the result

---

### Post by dwhitney67 on 2012-11-21
> **NixForFree said:**
> 
The problem, however, is definitely the first strok with NULL as an argument, which causes a segfault ONLY within the while-loop unless you "touche" the pointer by reading from it **first**. If I take the printf() line away the segfault is still the result

I'm not sure I understand the dilemma.  If you place two strtok() calls within the loop (skip every other number?), or even a single one, there's not problem.

You can experiment with this code to see for yourself:
```

#include <string.h>
#include <stdlib.h>
#include <stdio.h>

int main()
{
    const char* delim = ",";

    char* data = strdup("1,2,3,4,5");  /* make copy; we can't manipulate string literal */

    char* p = strtok(data, delim);

    while (p)
    {
        p = strtok(NULL, delim);

        if (p) printf("%d ", atoi(p));

        p = strtok(NULL, delim);
    }
    printf("\n");

    return 0;
}

```

---

### Post by NixForFree on 2012-11-21
[LEFT]Thank you, dwhitney67, you were right and your input has driven me to the solution: 

The pointer p is set to NULL at the end. If strtok is put after printf, the while-loop terminates, if it is put before printf, NULL is fed into atoi which isn't happy with the argument. 
(I still don't know why that happened as well when I took the printf away, but anyway, all's fine now.)

 ```

#include <stdio.h> 
#include <stdlib.h> 
#include <string.h>  
int main (void){
     FILE *f;
     char *p, temp[255];
     f=fopen("/home/user/file.csv","r");
     fgets(temp,255,f);  /* temp contains "12.23.34, 10, 22, 34, 45, 118, 337" now */          
     p=strtok(temp,",");
     while(p!=NULL){
           **p=strtok(NULL,",");  // finally p= NULL => fed into atoi results in segfault**
           printf("%d ",atoi(p)); //this line needs an "if(p)" prepended.
      }
 return EXIT_SUCCESS; 
} 
```[/LEFT]

---

