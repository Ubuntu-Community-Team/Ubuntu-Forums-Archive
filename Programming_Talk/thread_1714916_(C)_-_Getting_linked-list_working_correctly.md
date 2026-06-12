---
title: "(C) - Getting linked-list working correctly"
date: 2011-03-26
forum: Programming Talk
---

### Post by trilobite on 2011-03-26
Hi all - 
 I'm doing a simple linked-list in C. 
The code is below. It compiles, but it simply prints out the number "42" four times, instead of printing 42, 5, 7, 10. 
```
 

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <math.h>
#include <malloc.h> 

typedef struct node { 
   int val;    
   struct node *next;     
} list; 

list *add_val(list *l, int myint)
{ 
   list *nl = malloc(sizeof(list)); 
   l->next = nl; 
   nl->val = myint; 
   nl->next = NULL;    
   return nl;      
}     

int main(int argc, char *argv[])
{    
 list a;     
 a.val = 42;  
 a.next = NULL; 
  
 add_val(&a, 5); 
 add_val(&a, 7);  
 add_val(&a, 10); 
 int i; 
 
 for(i=0; i<4; i++)    
  {
    printf("Value: %d \n", a.val );  
  }
      
 return 0;     
}

``` 

I'm not sure why the code isn't printing all of the values, so any help to fix this would be great. Many thanks in advance - 
- trilobite

---

### Post by Some Penguin on 2011-03-26
```

 for(i=0; i<4; i++)    
  {
    printf("Value: %d \n", a.val );  
  }

```

Isn't it pretty obvious that **a** doesn't change during the loop and that a.val will be printed four times in a row?

Also, your add() method is pretty borked.  Draw what it does on paper (what's passed into the method and how it changes, step by step) and it should be pretty clear why.

---

### Post by cap10Ibraim on 2011-03-26
there is an error building the list and an error iterating through it 
do you want to add elements at the beginning or the end ?

---

### Post by schauerlich on 2011-03-26
It helps to draw out figures.

First, you make a new node, and put 42 in it. So far, so good.

```
(42)
```

Then, you make the 42 point to a new node, and you fill that node with a 5.

```
(42) -> (5)
```

Then, you take that same original 42, and instead of making it point to what it used to point to, you make a new node and make the 42 point to it. You then put a 7 there.

```
(42)    (5)
 |
 + ---> (7)
```

Then, you do the same thing, making it point to a new node with 10.

```
(42)    (5)
 |
 |      (7)
 |
 + ---> (10)
```

Then, at the end, you print out "42" because you only ever ask for the value at the head of the list, that is, "a". If you want to add things on to the end of the list, you have to find the end of the list first. You can do this by following the 'next' pointer in each node until you find one that points to null. Then, make that pointer point to your new node.

---

### Post by trilobite on 2011-03-26
Hi again - 
 Thanks very much for your replies, Some Penguin, cap10Ibraim and schauerlich -  
they're very helpful! It shouldn't take me long now to get this working. 
Bye for now - 
- trilobite

---

