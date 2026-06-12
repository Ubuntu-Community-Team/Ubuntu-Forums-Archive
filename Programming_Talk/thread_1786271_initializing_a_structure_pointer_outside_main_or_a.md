---
title: "initializing a structure pointer outside main or a function"
date: 2011-06-19
forum: Programming Talk
---

### Post by jamesbon on 2011-06-19
Here is a small code .It is not working code with features but you can compile to understand my question.

```
#include<stdio.h>
#include<stdlib.h>
struct node {
int data;
struct node  *next;
};
[B]struct node * list,*root;
list=NULL;
root=NULL;
[/B]struct node * create_node(int );
int main ()
{
int i,j,choice;
printf("Enter a number this will be root of tree\n");
scanf("%d",&i);
printf("Give us choice 1 to enter more numbers 0 to quit\n");
scanf("%d",&choice);
switch (choice)
        {
        case 1:break;

        case 2:break;
        }
}
// end of function main
struct node * create_node(int data)
{
struct node *temp;
t    emp = (struct node *)malloc(sizeof(struct node));
return temp;
}
```
When I compiled above code  got following error

```
kbc.c:10: warning: data definition has no type or storage class
kbc.c:10: error: conflicting types for ‘list’
kbc.c:9: note: previous declaration of ‘list’ was here
kbc.c:10: warning: initialization makes integer from pointer without a cast
kbc.c:11: warning: data definition has no type or storage class
kbc.c:11: error: conflicting types for ‘root’
kbc.c:9: note: previous declaration of ‘root’ was here
kbc.c:11: warning: initialization makes integer from pointer without a cast

```

Now I came following solutions

1) initializing of structure pointers like I did above is wrong and should be done in main() or in a function definition.

2) I replace 
```
struct node * list,*root;
list=NULL;
root=NULL;

``` 
by following lines

```
struct node *list=NULL;
 and struct node *root=NULL
```
and then compile I do not get error.
I want to know why these 2 solutions I mentioned work and what is wrong with the approach which was giving me error?

---

### Post by JupiterV2 on 2011-06-20
Because, in the global space (outside any functions) you may not do anything but make variable/function declarations. The C standard allows you to assign a value in a type declaration only in the global space.

```
#include <stdio.h>
int x = 0; /* valid, declare a global variable */
x = 1; /* invalid, compiler error */

int main (void)
{
  printf ("%d\n, x);
  return 0;

```

While in some cases unavoidable, it is generally discouraged to use global variables. If a variable is to be global only to a specific file then you should use the 'static' keyword.

---

