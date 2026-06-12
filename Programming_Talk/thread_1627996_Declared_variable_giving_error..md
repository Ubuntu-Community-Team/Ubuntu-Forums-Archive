---
title: "Declared variable giving error."
date: 2010-11-22
forum: Programming Talk
---

### Post by c2tarun on 2010-11-22
[PHP]
#include<stdio.h>
#include<stdlib.h>
#include<math.h>

struct stry
{
  int min;
  int max;
};
typedef struct stry stry;

struct strx
{
  int value;
  stry* next;
};
typedef struct strx strx;


void insert(strx* node,int n)
{
  //stry* start;
  stry* new;
  new=node->next;
  
  if(new == NULL)
    {
    new=(stry*)malloc(sizeof(stry));
    new->min=99999;
    new->max=-1;
    }

  if(new->min > n)        // this is line number 36
    min=n;
  if(new->max < n)
    max=n;
  node->next=new;
  return ;
}
[/PHP]this is the small part of a long code. i have main function calling this function.
i m getting this error:

```

points.c:36: error: &#8216;min&#8217; undeclared (first use in this function)

```can anyone please explain why i am getting this error, as i declared the variable in struct stry and also allocated memory for it.

---

### Post by Arndt on 2010-11-22
> **c2tarun said:**
> [PHP]
#include<stdio.h>
#include<stdlib.h>
#include<math.h>

struct stry
{
  int min;
  int max;
};
typedef struct stry stry;

struct strx
{
  int value;
  stry* next;
};
typedef struct strx strx;


void insert(strx* node,int n)
{
  stry* start;
  stry* new;
  start=node->next;

  if(start == NULL)
    {
    new=(stry*)malloc(sizeof(stry));
    new->min=99999;
    new->max=-1;
    }

  if(new->min > n)        // this is line number 36
    min=n;
  if(new->max < n)
    max=n;
  node->next=new;
  return ;
}
[/PHP]
this is the small part of a long code. i have main function calling this function.
i m getting this error:

```

points.c:36: error: ‘min’ undeclared (first use in this function)

```can anyone please explain why i am getting this error, as i declared the variable in struct stry and also allocated memory for it.

Yes, new->min works, but on the erroneous line you have plain 'min'. If you mean new->min, you have to write that. Otherwise the compiler takes it as a reference to a local or global variable, which hasn't been declared.

---

### Post by c2tarun on 2010-11-22
> **Arndt said:**
> Yes, new->min works, but on the erroneous line you have plain 'min'. If you mean new->min, you have to write that. Otherwise the compiler takes it as a reference to a local or global variable, which hasn't been declared.

```


  if( **new->min** > n)
    min=n;
  if( new->max < n)
    max=n;


```i allready wrote there new->min, see. is anything wrong???


i m extremely sorry.. i got it :D

---

### Post by c2tarun on 2010-11-22
i m very sorry folks.
it was very silly mistake i did and posted on the forum
sorry

---

