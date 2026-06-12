---
title: "declaration a variable in one file and initializing in another C program"
date: 2010-11-25
forum: Programming Talk
---

### Post by jamesbon on 2010-11-25
I made 2 files which are different from the program above 
one is temp1.h and another is temp2.c to understand how extern is used.
So here is temp1.h 
```
#include<stdlib.h>
typedef struct node * bond;
extern int jk;
```
and temp2.c is 
```
#include<stdio.h>
#include<temp1.h>
struct node {
int data;
};
int main ()
{
bond t1;
t1=(bond)malloc(sizeof(bond));
t1->data=23;
printf("the data is %d\n",t1->data);
jk=0;
printf("The variable jk = %d\n",jk);
}

```                                                                                                                                                       
and when I compile these as 
```
cc -I ./ temp2.c 
``` then I get 
```
/tmp/ccdeJCat.o: In function `main':
temp2.c:(.text+0x3c): undefined reference to `jk'
temp2.c:(.text+0x46): undefined reference to `jk'
collect2: ld returned 1 exit status

```                 
I had declared jk in temp1.h as an extern int so why can I not initialize it in temp2.c?

---

### Post by worksofcraft on 2010-11-25
> **jamesbon said:**
> ...
I had declared jk in temp1.h as an extern int so why can I not initialize it in temp2.c?

Cuz you have to tell the compiler to actually allocate some memory to your jk variable somewhere.

Al you dun so far is told it that it exists and you tried to assign a value of zero to it. But the compiler ain't been told to actually allocate one.

You can probably fix it as follows:
[php]
#include<stdio.h>
#include<temp1.h>
struct node {
    int data;
};

int jk; // this is where we want to store this int

int main () {
    bond t1 = (bond) malloc(sizeof(node));
    t1->data=23;
    printf("the data is %d\n", t1->data);
    jk=0;
    printf("The variable jk = %d\n",jk);
}
[/php]

p.s. I realize you don't have to declare it in your header file in this case but
if you wanted to access the **SAME** variable jk from  separate .c files that are linked together to make the same program then you would!

---

### Post by jamesbon on 2010-11-25
> **worksofcraft said:**
> 
if you wanted to access the **SAME** variable jk from  separate .c files that are linked together to make the same program then you would!
Yea that is what I want to achieve and I have checked it by making a third c program printing the jk's value from this way as you suggested and it works exactly the same way you said.Now I am wondering why do we actually use a keyword extern at all?

---

### Post by debsankha on 2010-11-25
Don't use extern at all, just declare as int in your header file and you will be fine.

---

### Post by StephenF on 2010-11-25
> **debsankha said:**
> Don't use extern at all, just declare as int in your header file and you will be fine.
No you won't if the header file is included in more than one .c file of a program. It will fail at the linking stage due to two or more identical symbols existing. Which one is supposed to be linked to?

Ideally only definitions go in .h files and preferably not full structure definitions to keep program inter layer access under control.

---

### Post by jamesbon on 2010-11-25
Ohhh ok now I get your point.Thanks buddy.

---

