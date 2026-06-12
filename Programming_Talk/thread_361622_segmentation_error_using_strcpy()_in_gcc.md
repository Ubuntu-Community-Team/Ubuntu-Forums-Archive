---
title: "segmentation error using strcpy() in gcc"
date: 2007-02-14
forum: Programming Talk
---

### Post by lee797 on 2007-02-14
Can anyone explain what I am doing wrong in the create_node function below?
I get the following error when I run the program through dbg :

Program received signal SIGSEGV, Segmentation fault.
0xb7e69723 in strcpy () from /lib/tls/i686/cmov/libc.so.6

I assume I am using strcpy incorrectly, but I don't know why. The program implements a linked list of structures, originally written in Borland C++ builder and worked fine on windows. Any help would be much appreciated.
 
```
   /* node for list of string 'variables' */
  typedef struct str_node
  {
     char *value;
     char name;
     struct str_node *next;
  } node;


  node* create_node(char *str, char *n)
  {
      node *p;

      p = (node*) malloc(sizeof(node));
      p->next = NULL;
      strcpy(p->value, str);   /* error arises here */
      p->name = *n;

      return p;
  } /* end create_node */
```

---

### Post by hod139 on 2007-02-14
Before I comment on the error, let me say a few things.  You stated that this was C++ code, but it looks suspiciously like C code to me.  Is this a C or C++ project?  You should post your code inside a code block to make it more readable.  You shouldn't be using strcpy ever, but before posting solutions I would like to know which language, C or C++ you are trying to do this in, because the solution would differ based on the language.

---

### Post by lee797 on 2007-02-14
My apologies, it is indeed c code, however it was originally compiled in
C++ Builder (as C) as that is the program we use in my college. Regarding the code
readability - yes I just noticed that feature, sorry about that.

---

### Post by hod139 on 2007-02-14
Ok, here is some code that works, followed by an explanation

```

#include <stdlib.h>
#include <string.h>
#include <stdio.h>

 /* node for list of string 'variables' */
typedef struct str_node
{
   char *value;
   char name;
   struct str_node *next;
} node;


node* create_node(char *str, char n, int len)
{

   node *p;

   p = (node*) malloc(sizeof(node));
   p->next = NULL;
   p->value = (char*) malloc(len * sizeof(char)); /* allocate room for the string */
   strncpy(p->value, str, len); /* use strncpy, not strcpy, for extra safety */
   (p->value)[len-1] ='\0'; /* null terminate for even more safety */
   p->name = n;

   return p;
} /* end create_node */

int main(void)
{
   node* a_node = create_node("string value", 'a', 13);
   printf("a_node->value = %s \n", a_node->value);
   return 0;
}

```The problem with your code is that you were not allocating space for the nodes string value before trying to set it.  In the code I posted, I pass the size of the string as a third input to the create_node function, and I malloc the node's string based on that size.  Then I use strncpy instead of strcpy to copy the string into the newly allocated space. The function strncpy is safer than strcpy because it will copy only N bytes instead of checking for a null terminator, but it isn't perfect.  This is why on the subsequent line I null terminate the string for safety.  This protects against someone passing a string larger than len, and doesn't hurt if the string is the correct length, since strings are null terminated anyways.

Lastly, I changed the char n parameter to pass by value, since it is only a char and no need to complicate things by passing a pointer.

I also added a small main just to test it out.  And you can see that passing a string with length longer than len is still safe, since I null terminate it manually.

If you have any other questions about the code, just post back.

---

### Post by lee797 on 2007-02-14
No questions, thanks for your help.

---

