---
title: "qsort and bsearch issues. Need some help"
date: 2012-07-07
forum: Programming Talk
---

### Post by spanlength1 on 2012-07-07
Hi , I am doing a small assignment which involves function pointers and qsort and bsearch. I will first put the material given then my solution and finally the issues i am facing.

```

#ifndef TKK_AS_C_SORT_FUNCTIONS
#define TKK_AS_C_SORT_FUNCTIONS

/* Compare two strings lexically (ASCII value-wise, same as strcmp())
 * The string "duck" is before "rabbit" in this order but
 *  "Rabbit" is before "duck" (see an ASCII chart)
 * IMPORTANT: Note that the parameters are ** and not *
 *  this is because qsort and bsearch operate on pointers to data.
 * Thus, when data is char*, a pointer to this data is char**.
 * Returns: 0 if the two strings are equal
 *          <0 if r > l
 *          >0 if l > r
 * Hint: strcmp */
int compareLexical(const char** l, const char** r);

/* Sorts an array of strings using the given order predicate (compare function)
 * The string array is assumed to contain a terminating NULL character 
 * The order predicate is of the same type as compareLexical and compareNumerical.
 * IMPORTANT: use the qsort function for sorting the array */
void sortStrings(char **strings, /* TODO: Insert the order predicate here */);

/* Finds a string from a sorted array of strings
 * The order predicate and the string array are identical to the sortStrings function.
 * Returns: Whatever bsearch returned.
 * IMPORTANT: use the bsearch function for finding the string. Really, you have
 *  to use it, there is no alternative here. */
char** findString(char **strings, const char *str, /* TODO: Insert the order predicate here */);

#endif

```

```
#include "functions.h"

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(void)
{
  char buffer[512];

  char **strings = malloc(sizeof(void*));
  size_t nStr = 0;

  printf("Please input strings (empty line terminates)\n");
  
  while (1)
  {
    fgets(buffer, 512, stdin);
    if (*buffer == '\n')
      break;
    if (strchr(buffer, '\n'))
      *strchr(buffer, '\n') = '\0';
    strings = realloc(strings, (nStr + 2) * sizeof(char*));
    strings[nStr++] = strcpy(malloc(strlen(buffer) + 1), buffer);
  }
  strings[nStr] = NULL;
  printf("Read %zu string(s)\n", nStr);

  printf("Sorting lexically and printing\n");
  sortStrings(strings, compareLexical);
  for (size_t i = 0;i < nStr;i++)
    puts(strings[i]);

  printf("Please enter search string\n");
  fgets(buffer, 512, stdin);
  if (strchr(buffer, '\n'))
     *strchr(buffer, '\n') = '\0';
  printf("\"%s\" %sfound\n", buffer, findString(strings, buffer, compareLexical)?"":"not ");
  
  printf("Cleaning up and terminating\n");
  for (size_t i = 0;i < nStr;i++)
    free(strings[i]);
  free(strings);
}
```

My solution. I modified the header file function signatures to below 
```

void sortStrings(char **strings, int (*)(const char **,
                     const char **));

char** findString(char **strings, const char *str, int (*)(const char **,
                     const char **));

```

I am getting some warnings in this which I post below. I am not sure how to get rid of them because i cannot modify the function signatures of compareLexical.
Below is my code.
```

#include <string.h>
#include <stdio.h>
#include <stdlib.h>
#include "functions.h"


int compareLexical(const char** l, const char** r){
    int value = strcmp(*l ,*r);
    return value;
}

void sortStrings(char **strings, int (*comp)(const char **,
                     const char **)){
    int count = 0;
    do {
        count++;
    }while ( strings[count] != NULL );
    printf("Value of count is  %d \n",  count );
    qsort(strings,count,sizeof(char*),comp);

}

char** findString(char **strings, const char *str, int (*comp)(const char **,
                     const char **)){
    int count = 0;
    do {
        count++;
    }while ( strings[count] != NULL );
    printf("Value of count is  %d \n",  count );
    char **ptr = bsearch(str, strings, count, sizeof(char*), comp);
    return ptr;
}


```

I am getting segmentation error in the findString function.
Also i get warning if i compile using the -std=c99 -pedantic -Wall -Wextra -g command.

Please give your inputs and sujjestions.

---

### Post by Bachstelze on 2012-07-07
You should read man pages more carefully. ;)

> 
[font=monospace]DESCRIPTION
     The bsearch() function searches an array of nel objects, the initial member of which is pointed to by base, for a member that matches **the object pointed to by key**.  The size (in bytes) of each member of the array is specified by width.

     The contents of the array should be in ascending sorted order according to the comparison function referenced by compar.  The compar routine is expected to have two arguments which point to the key object and to an array member, in that order.  It should return an integer which is less than, equal to, or greater than zero if the key object is found, respectively, to be less than, to match, or be greater than the array member.
[/font]


So

```
char **ptr = bsearch(&str, strings, count, sizeof(char*), comp);
```

As for the warnings, I guess you can ignore them. Be sure to let your instructor know that his code is wrong.

---

### Post by spanlength1 on 2012-07-08
> **Bachstelze said:**
> You should read man pages more carefully. ;)



So

```
char **ptr = bsearch(&str, strings, count, sizeof(char*), comp);
```

As for the warnings, I guess you can ignore them. Be sure to let your instructor know that his code is wrong.

Thanks for the information. Its now working fine. I am facing with a small issue , regarding the function where i sort them numerically. 

```

/* Same as compareLexical but compares the strings numerically.
 * The string "123duck" is after "99rabbit" in this order.
 * IMPORTANT: This ordering assumes that the strings begin with an integer,
 *  strings that do not, are assumed to have the value zero.
 * Thus, "0bird" and "bird" are equal in value with this assumption.
 * Hint: sscanf */
int compareNumerical(const char** l, const char** r){
    int *lvalue =0;
    int *rvalue = 0;
    char *lchar = NULL;
    char *rchar = NULL;
    sscanf(*l,"%d%s",lvalue,lchar);
    sscanf(*r,"%d%s",rvalue,rchar);
    if(lvalue>rvalue) return 1;
    else if(lvalue<rvalue) return -1;
    else return 0;
}
```

I am getting seg error while running this in the main function. The code in main.c is below:
```
  printf("Sorting numerically and printing\n");
  sortStrings(strings, compareNumerical);
  for (size_t i = 0;i < nStr;i++)
    puts(strings[i]);
```

Please tell me where i am doing wrong.

---

### Post by Bachstelze on 2012-07-08
You are only defining pointers, you are not allocating memory for the actual objects. Also, you do not use lchar and rchar...

```
int compareNumerical(const char** l, const char** r){
    int lvalue = 0;
    int rvalue = 0;
    sscanf(*l,"%d",&lvalue);
    sscanf(*r,"%d",&rvalue);
    if(lvalue>rvalue) return 1;
    else if(lvalue<rvalue) return -1;
    else return 0;
}
```

---

