---
title: "this code works in one compiler, doesn't work in another"
date: 2014-10-15
forum: Programming Talk
---

### Post by IAMTubby on 2014-10-15
I was trying to populate an array using a pointer and it's given me a few results which I'm finding difficult to comprehend. I'm sorry for the long post, and I have tried to figure out the possible reasons, but every time I try something, it throws up something new.(Sorry also, for the smiley in the question, I didn't mean to put it there and am not able to edit it now, so let it be :) ) 
The array name **'l'** used in the questions below signifies it's a local pointer - l for local.

1. This code works in one compiler, doesn't work in another
I understand that it's basically because on the one where it works, the address of l is not null, and yes null in the other one. 
My question basically is, how do I access an array using pointers/ 
```

#include <stdio.h>
#include <malloc.h>


int main(void)
{
 int* l;
 int  i =0;

 /* I did try printing out the address here and check on both machines - As expected, it gives null on the machine where the code gives a seg fault, and not null in the machine where it works */
 printf("l == [%p]\n",l);


 for(i=0;i<10;i++)
  *(l+i) = i+1;


 for(i=0;i<10;i++)
 printf("%d ",l[i]);


 return 0;
}

```


2.Now consider this code where I have only added one more pointer in the exact same place where I had used l in the previous example. This gives me a seg fault even in the machine where the previous code was working. Wow!
```

#include <stdio.h>
#include <malloc.h>


int main(void)
{
 int* l1;
** int* l2;**
 int  i =0;


 /* I did try printing out the address here and check on both machines */
 printf("l1 == [%p]\n",l1);
** printf("l2 == [%p]\n",l2);**


 for(i=0;i<10;i++)
 {
  *(l1+i) = i+1;
**  *(l2+i) = i+1;**
 }


 for(i=0;i<10;i++)
 {
  printf("%d ",l1[i]);
**  printf("%d ",l2[i]);**
 }


 return 0;
}


``` 
This is the  output I get
[B]l1 == [0x400410]l2 == [0x7ffffb090b90]
Segmentation fault (core dumped)
[/B]

3.And now, what's the default address a pointer points to ? I think it is : 
Default value of local pointer = random address,
Default value of global pointer = NULL,
Am I correct?

4.Realizing that code in 1 does not work for one of the compilers because it takes the value as NULL, I tried to malloc addresses before putting in values. Please can you tell me how it's done. I tried doing it(see code below), but this it gives me : **error: lvalue required as left operand of assignment**
#include <stdio.h>
#include <malloc.h>


int main(void)
{
 int* l1;
 int  i =0;


 /* I did try printing out the address here and check on both machines */
 printf("l1 == [%p]\n",l1);


 for(i=0;i<10;i++)
 {
  (l1 + i) = malloc(200 * sizeof(char));
  *(l1+i) = i+1;
 }


 for(i=0;i<10;i++)
 {
  printf("%d ",l1[i]);
 }


 return 0;
}

Please advise.
And once again, sorry for the long post.

---

### Post by achuthpnr on 2014-10-16
You are going in the right direction. You need to allocate the memory before entering the loop such that you have 10 free pointers (since you go from i=0 to 9). Later in the loop you assign them the memoy address where the value is stored. Also, if you want to have a null pointer array initially, use calloc instead of malloc.

Hope it gives some direction as I dont have the intrisnsic skills to explain things.

---

### Post by ofnuts on 2014-10-16
You have to start by allocating the l1 array. If the array is small and temporary, you can allocate it statically in the stack:

```
int l1[10];  // For ten ints
```

If the array is big or should be passed around  (in particular to some code that calls you), then you allocate it:

```
int *l1=calloc(2000,sizeof (int)); // for 2000 ints
```

If your array is an array to pointers to more arrays this becomes:

```

int *l1[10]; // 10 pointers to int
int **l1=calloc(2000,sizeof (int *)); // for 2000 pointers to int

```

And then with either allocation styles:
```

l1[0]=calloc(2000,sizeof (int)); // allocating array of int, storing pointer in array of pointer to int.
l1[0][3]=12; // 4th integer in first array set to 12

```

---

### Post by IAMTubby on 2014-10-17
> **ofnuts said:**
> 
```
int *l1=calloc(2000,sizeof (int)); // for 2000 ints
```
ofnuts, thanks for the reply.
How would I rewrite this for malloc'ing an array where I'm planning to have no more than 10 integers?
Would int *l1=malloc(10 * sizeof(int)); do? Please see the code below.
```

#include <stdio.h>


int main(void)
{
 int* l;
 int i = 0;


 l = malloc(10 * sizeof(int));


 for(i=0;i<10;i++)
 {
  *(l+i) = i+1;
 }


 for(i=0;i<10;i++)
  printf("%d ",*(l+i));


 return 0;
}

```

I have a couple of questions though : 
1. If I'm planning to have 10 integers, is it enough to do int*  l = malloc(10 * sizeof(int)); ? What I'm asking is, don't I have to do something like
```

for(i=0;i<10;i++)
{
 l + i = malloc(sizeof(int));
}

```
(which gives an lvalue error.)

2.Isn't a local pointer supposed to hold a random address when initialized as opposed to a global pointer which holds NIL? But what I observe is that both show NIL. Is this correct?
#include <stdio.h>

```

char* g;
int main(void)
{
 char* l;


 printf("l == [%p]\n",l);//l == [(nil)]
 printf("g == [%p]\n",g);//g == [(nil)]


 return 0;
}

```

---

### Post by ofnuts on 2014-10-17
> **IAMTubby said:**
> ofnuts, thanks for the reply.
How would I rewrite this for malloc'ing an array where I'm planning to have no more than 10 integers?
Would int *l1=malloc(10 * sizeof(int)); do?

yes, but using calloc() is somewhat better (more readable, and you get a default initialization)


 
> **IAMTubby said:**
> ofnuts, thanks for the reply.
I have a couple of questions though : 
1. If I'm planning to have 10 integers, is it enough to do int*  l = malloc(10 * sizeof(int)); ? What I'm asking is, don't I have to do something like
```

for(i=0;i<10;i++)
{
 l + i = malloc(sizeof(int));
}

```
(which gives an lvalue error.)

See the defintion of an "lvalue" in C... 

The big assumption of arrays is that they are in contiguous memory, so you have to allocate them in one call. If  you use several calls they can be scattered in memory and this assumption doesn't hold.


> **IAMTubby said:**
> ofnuts, thanks for the reply.
2.Isn't a local pointer supposed to hold a random address when initialized as opposed to a global pointer which holds NIL? But what I observe is that both show NIL. Is this correct?
#include <stdio.h>


A local pointer often just contains what was in the stack, but some compiler options may generate code to initialize it (but this happens each the function is entered... Global data is initialized once a part of the program loading.

But you shouldn't really care... you can't depend on what is in variables you haven't explicitly set. If you want a variable to hold null, initialize it to NULL in the declaration.

---

### Post by IAMTubby on 2014-10-17
> **ofnuts said:**
> 
A local pointer often just contains what was in the stack, but some compiler options may generate code to initialize it (but this happens each the function is entered... Global data is initialized once a part of the program loading.

But you shouldn't really care... you can't depend on what is in variables you haven't explicitly set. If you want a variable to hold null, initialize it to NULL in the declaration.
Thanks ofnuts, so always allocate memory(malloc/calloc) irrespective of whether it is local or global? Can I conclude that way?

---

### Post by IAMTubby on 2014-10-17
> **achuthpnr said:**
> 
Hope it gives some direction as I dont have the intrisnsic skills to explain things.
Yes achuthpnr, it does. Thank you.

---

### Post by ofnuts on 2014-10-17
> **IAMTubby said:**
> Thanks ofnuts, so always allocate memory(malloc/calloc) irrespective of whether it is local or global? Can I conclude that way?

No... small local can be allocated on the stack... easier for you, and faster to execute...

---

