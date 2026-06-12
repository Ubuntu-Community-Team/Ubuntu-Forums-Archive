---
title: "need help with c++ in ubuntu"
date: 2010-09-21
forum: Programming Talk
---

### Post by c2tarun on 2010-09-21
hi friends
i am using Code:Block ide.

i made a program and used a structure there


struct key
{
    int p8[10]={6,3,7,4,8,5,10,9};
    int p10[10]={3,5,2,7,4,10,1,9,8,6};
    int k1[10];
    int k2[10];
};


this is the error i m getting
/home/tarun/Documents/Programs/subkey.c|6|error: expected &#8216;:&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;}&#8217; or &#8216;__attribute__&#8217; before &#8216;=&#8217; token|
this error is in the first line of variable declaration

can anyone please explain y?

---

### Post by Mordred on 2010-09-21
You should not assign values in your struct declaration.
If you need default values, provide an init function to
assign them.

[PHP]
struct key
{
int p8[10];
int p10[10];
int k1[10];
int k2[10];
};
[/PHP]

Should compile.

---

### Post by dwhitney67 on 2010-09-21
Just to follow up on Mordred's post, this should also compile:
```

struct key
{
int p8[10];
int p10[10];
int k1[10];
int k2[10];
};


int main()
{
   key k = { {1,2,3,4,5,6,7,8,9,0},
             {0,9,8,7,6,5,4,3,2,1}
           };

   ...
}

```

---

### Post by c2tarun on 2010-09-21
#include<stdio.h>

struct key
{
    int p8[10];
    int p10[10];
    int k1[10];
    int k2[10];
};

void permute8(int *k,struct key *key1)
{
    int temp[10],i;
    for(i=0;i<8;i++)
    {
        temp[i]=*(k+key1->p8[i]-1);
    }
    for(i=0;i<8;i++)
        *(k+i)=temp[i];
}

void permute10(int *k,struct key *key1)
{
    int temp[10],i;
    for(i=0;i<10;i++)
    {
        temp[i]=*(k+key1->p10[i]-1);
    }
    printf("program is here2\n");
    for(i=0;i<10;i++)
    {
        *(k+i)=temp[i];
    }
}


struct key *subkey(int k[])
{
    int temp,i;
    struct key k1;
    printf("program is here1\n");
    permute10(&k[0],&k1);
    for(i=0;i<10;i++)
        printf("%d ",k[i]);
    return &k1;
}


int main()
{
    int k[10],i;
    struct key key1={{6,3,7,4,8,5,10,9},{3,5,2,7,4,10,1,9,8,6}};
    struct key *keyp;
    for(i=0;i<10;i++)
    {
        scanf("%d",&k[i]);
    }
    keyp=subkey(k);
    return 0;
}








above is the complete new program
this program is working fine over turbo c++ over windows but giving an SEGMENTATION FAULT error when running in gcc on ubuntu.

please help.
thanx

---

### Post by c2tarun on 2010-09-21
bump

---

### Post by dwhitney67 on 2010-09-21
turbo C++ shouldn't be trusted.

The problem with your code is that you are returning the address of a local variable that has been destroyed the moment this function returns:
```

struct key *subkey(int k[])
{
int temp,i;
struct key k1;
printf("program is here1\n");
permute10(&k[0],&k1);
for(i=0;i<10;i++)
printf("%d ",k[i]);
return &k1;
}

```

Now, as for your coding techniques, I see two possibilities... either 1) you are referencing some god-awful book, or 2) you studied C in your previous life and are trying to incorporate that knowledge into a C++ program.

If I guessed right with choice 2, then I suggest you toss your C knowledge aside, and study pure C++.

EDIT:  Another possibility... you are confusing C++ with C.  Your program is pure C.


P.S.  In the future, please post your code within CODE tags.

---

### Post by dwhitney67 on 2010-09-21
> **c2tarun said:**
> bump

Btw, it would be helpful if you would indicate what is it that you are attempting to accomplish.

The program you posted is replete with bugs.  Initially I thought it only had one bug, but there are definitely others.

---

### Post by c2tarun on 2010-09-21
> **dwhitney67 said:**
> Btw, it would be helpful if you would indicate what is it that you are attempting to accomplish.

The program you posted is replete with bugs.  Initially I thought it only had one bug, but there are definitely others.



thanks for replying
i was making the program for subkey generation in DES algorithm, this is not complete code.
you are right i fall in you 2nd category. i studied c long time back and now trying to use it again.
i accept that i m returning the address of a local variable that is getting destroyed at the moment, for this i can use a global variable for the structure. but the point is this is working as expected with turbo c++ compiler in windows environment. are there any flaws in that compiler. and please tell me is there any way to protect local variables from not getting destroyed. 
thanx a lot for replying.
waiting for further guidance

---

### Post by dwhitney67 on 2010-09-21
This [DES code]("http://ubiqx.org/libcifs/source/Auth/DES.c") (for encryption) is readily available; will it not help you?

Here's another [link]("http://www.ussrback.com/crypto/aes/des/des.c.html") that covers both encryption and decryption.

---

### Post by c2tarun on 2010-09-21
sir i was trying to implement the code by myself. as a practice to improve my coding techniques. please help

---

### Post by dwhitney67 on 2010-09-21
I do need to go to bed... I do have a job, that pays well, and I wish I could say the same about this forum.

But just to get you going, take this code and augment it.
```

#include <stdio.h>
#include <stdlib.h>

struct key
{
   int p8[10];
   int p10[10];
   int k1[10];
   int k2[10];
};


void permute10(int* k, struct key* key1)
{
   // above, k is a pointer to an int value

   int temp[10];

   for (int i = 0; i < 10; ++i)
   {
      temp[i] = *(k + key1->p10[i] - 1);  // note key1's data is accessed, but this data has not been initialized!!!
   }

   for (int i = 0; i < 10; ++i)
   {
      *(k+i) = temp[i];   // assigning to k as if it were an array?  maybe p8??
   }
}

struct key* subkey(int k[])
{
   struct key* k1 = malloc(sizeof(struct key));

   permute10(&k[0], k1);  // address of k[0]??
                          // k1 has not been initialized with any data!

   return k1;
}


int main()
{
   // not currently used
   //struct key key1={{6,3,7,4,8,5,10,9},{3,5,2,7,4,10,1,9,8,6}};

   int k[10];

   for (int i = 0; i < 10; ++i)
   {
      printf("Enter value %d: ", i + 1);
      scanf("%d", &k[i]);
   }

   struct key* keyp = subkey(k);

   return 0;
}

```

Now whether or not this code does what you want is debatable.

PS. #1  As I stated earlier, always post code in CODE tags.  Also be nice to fellow coders and readers of your code by inserting appropriate white-space in the code so as to make it more readable.

PS. #2  The code above was written for ISO C 1999 standards.  Adjust your compiler if necessary to deal with it.

---

### Post by c2tarun on 2010-09-21
sir thanx for helping so far.
i am new to ubuntu and this forum as well.
i was unaware of the protocols
i'll take care from the next time

---

