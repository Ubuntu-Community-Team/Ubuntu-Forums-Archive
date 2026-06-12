---
title: "Segmentation fault when using gcc"
date: 2011-08-08
forum: Programming Talk
---

### Post by NotGeek on 2011-08-08
// Thank you for Paul at #4, here's the solution. And it works at my PC
Well, the program is simple. I just want to sort some strings by an array of pointers.
I've searched the forum, and allocated memory for pointers. However, the bug is too
naughty and not vanish. Here is the code:
 
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
void stringSort(char* p[5])
{
 int i, j;
 char temp[100];
 for(i = 0; i < 5; i++)
 {
  for (j = 0; j < 5-i; j++)
/*   if (strcmp(p[j], p[j+1]))  // strcmp() function using incorrectly
 
   {
    *temp = *p[j];               // well, it's not correct here, see it at #4 by Paul
    *p[j] = *p[j+1];
    *p[j+1] = *temp;
   }
*/
if (strcmp(p[j], p[j-1]) < 0)    {
    strcpy(temp, p[j]);
    strcpy(p[j], p[j-1]);
    strcpy(p[j-1], temp);
   }
 }
 return;
}
int main()
{
 char* p[5];
 char temp[100];
 int i;
 
 for (i = 0; i < 5; i++)
 {
  scanf("%s", temp);
 // In some cases, the Segmentation fault come up without allocation 
  p[i] = (char*)malloc(sizeof(temp)+1);memery for a pointer
  strcpy(p[i], temp);
 }
 stringSort(p);
 for (i = 0; i < 5; i++)
 {
  printf("%s\n", p[i]);
 }
 return 0;
}
```
 
 
PS: my linux kenel version is 2.6.38-10

---

### Post by Joeb454 on 2011-08-08
Moved to **Programming Talk**

---

### Post by PaulM1985 on 2011-08-08
Just as a guess, this seems dodgy:

```

void stringSort(char* p[5])
{
 int i, j;
 char temp[100];
 for(i = 0; i < 5; i++)
 {
  for (j = 0; j < 5-i; j++)
   if (strcmp(p[j], p[j+1]))   // <- this line

```

If p is an array of 5 objects, i = 0 (we are in first i loop) and j = 4 (in last iteration of j loop), you are using p[j + 1], which is p[5], which is outside the bounds of p.

Also, I would look to either do string copying inside your if(strcmp()) part, or use pointers, not a mixture of both.  Your temp variable is an array of 100 chars, then you point it to look at something else ie, not the 100 chars that were initially allocated for it.  You may want to change temp to be char* temp, you keep it as it is and use strcpy().

Paul

---

### Post by NotGeek on 2011-08-08
> **PaulM1985 said:**
> Just as a guess, this seems dodgy:
 
```

void stringSort(char* p[5])
{
 int i, j;
 char temp[100];
 for(i = 0; i < 5; i++)
 {
  for (j = 0; j < 5-i; j++)
   if (strcmp(p[j], p[j+1]))   // <- this line

```
 
If p is an array of 5 objects, i = 0 (we are in first i loop) and j = 4 (in last iteration of j loop), you are using p[j + 1], which is p[5], which is outside the bounds of p.
 
Also, I would look to either do string copying inside your if(strcmp()) part, or use pointers, not a mixture of both. Your temp variable is an array of 100 chars, then you point it to look at something else ie, not the 100 chars that were initially allocated for it. You may want to change temp to be char* temp, you keep it as it is and use strcpy().
 
Paul
 
Thank you, Paul!  It's amazing that someone reply so quickly and solve my problem so perfectly although i have debug it indepently.

---

