---
title: "Deleting a character is string s1 that matches any character in string s2"
date: 2010-01-08
forum: Programming Talk
---

### Post by bhaskar_goel on 2010-01-08
I am trying to figure out the **C** code used for solving the problem mentioned in the Title ,but cant seem to figure it out.
  ```
void squeeze(char s1[],char s2[])
    { int i,j,k;
      for(i=k=0;s1[i]!='\0';i++){**//how does this loop delete chars in s1?**
               for(j=0;s2[j]!='\0' && s2[j]!=s1[i];j++)
                    ;
                  if(s2[j]=='\0')
                     s1[k++]=s1[i];
           }
      s1[k]='\0';
    }
```

How does the use of int k in the first for loop delete those chars in s1 that match any characters in s2?
Any hints?

---

### Post by Queue29 on 2010-01-08
Where did you find this atrocious code?

---

### Post by bhaskar_goel on 2010-01-08
Kernighan & Ritchie (C Prog)

---

### Post by worseisworser on 2010-01-08
Hint: you're assuming it *deletes* or *removes* characters.

---

### Post by bhaskar_goel on 2010-01-08
Delete or remove, the point is the characters that match in s1 are not there anymore if they match in s2.

---

### Post by dwhitney67 on 2010-01-08
Here's the code, rewritten with the all important white-space added.  K&R, as brilliant as they are, probably did not lay out the code in their book.  Oftentimes, publishers 'squeeze' code so that it fits on the pages of the book, and ultimately take up less pages.  This makes it harder for the customer (ie. reader) who purchased the book to make sense of anything.

@ the OP:  A little suggestion -- learn to use the space-bar and the <return> keys on your keyboard when writing code.  Spacing the code out makes it easier to read.
```

#include <stdio.h>

void squeeze(char s1[], const char s2[])
{
   int i,j,k;

   /*   loop for all characters in s1
    */
   for(i = k = 0; s1[i] != '\0'; ++i)
   {
      /*  loop for all characters in s2; break from loop when
       *  a match is found between a character in s2 and s1.
       */
      for(j = 0; s2[j] != '\0' && s2[j] != s1[i]; ++j);

      /*   check that we are not at the end of s2.  If not, then
       *   this implies that a character from s2 is in s1.
       */
      if (s2[j] == '\0')
      {
         /*   replace the character in s1, that is at position k,
          *   with the character in s1 that is at position i.
          *   Post-increment k for later use.
          */
         s1[k++] = s1[i];
      }
   }

   /*   set a null character in s1 at position k.  This marks the end
    *   of the s1 string.  This offers the illusion that the string has
    *   been squeezed, although in reality, the s1 string still occupies
    *   the same amount of space on the stack (or on the heap).
    */
   s1[k] = '\0';
}

int main()
{
   char       str1[] = "Hello World";
   const char str2[] = "lo";

   printf("before: %s\n", str1);

   /* remove characters from str1 that occur in str2 */
   squeeze(str1, str2);

   printf("after: %s\n", str1);

   return 0;
}

```

---

