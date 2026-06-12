---
title: "Call by value is not working properly"
date: 2010-12-18
forum: Programming Talk
---

### Post by c2tarun on 2010-12-18
I was trying to solve this problem:
[http://www.codechef.com/problems/MIXTURES/](http://www.codechef.com/problems/MIXTURES/)

this is my code:
[php]
#include<stdio.h>
#include<string.h>

char words[100000][2];
int n;  // number of words

int sum(int* p)
{
    int s=0,i;
    for(i=0;i<n;i++)
        s+=*(p+i);
    return s;
}

int func(int c, int check[])
{
    int i;
    check[c]=1;
    if(sum(&check[0]) != n)
    {
        for(i=0;i<n;i++)
        {
            if(check[i] == 0 && words[c][1] == words[i][0] )
            {
                func(i,check);
            //    check[i]=0;
            }
        }
    }
    else
    {
        if(sum(&check[0]) == n)
            return 1;
        else
            return 0;
    }
    return 0;
}

int main(void)
{
    char *temp=NULL;
    size_t strn=1000;
    int t; // number of test cases
    int check[100000];
    int templen;
    int i;  // loop variable
    memset(check,0,sizeof(check));
    getline(&temp,&strn,stdin);
    t=atoi(temp);
    while(t--)
    {
        getline(&temp,&strn,stdin);
        n=atoi(temp);
        for(i=0;i<n;i++)
        {
            getline(&temp,&strn,stdin);
            templen=strlen(temp);
            words[i][0]=*temp;
            words[i][1]=*(temp+templen-2);
        }

        for(i=0;i<n;i++)
        {
            if(func(i,check) == 1)
                break;
        }
        if(i<n)
            printf("Ordering is possible.\n");
        else
            printf("The door cannot be opened.\n");
    }
return 0;
}
[/php]
I don't know exactly what is wrong with my code.
check is a local variable to main, but I am copying check of main to a local check of function 'func'. problem is, i am only changing the value of local check of 'func' but that change is also reflected in main. Can anyone please tell me what is wrong in my code.
thanks

---

### Post by MadCow108 on 2010-12-18
your not copying it, you fell for one of the quirks of C:
int func(int c, int check[])
is the same as:
int func(int c, int * check)

so you pass the pointer to the original array and modify it

you need to explicitly copy it before or in the function e.g. by memcpy

---

### Post by saulgoode on 2010-12-18
> **c2tarun said:**
> I don't know exactly what is wrong with my code.
check is a local variable to main, but I am copying check of main to a local check of function 'func'. problem is, i am only changing the value of local check of 'func' but that change is also reflected in main. Can anyone please tell me what is wrong in my code.

Arrays are always passed by reference in C. This is because at compile time, the size of an array may not be known (whereas the size of structs, floats, ints, etc are fixed).

So when your 'func()' executes "check[c]=1", you are actually modifying main's local variable.

---

### Post by trent.josephsen on 2010-12-18
> **c2tarun said:**
> [php]
int sum(int* p)
{
    int s=0,i;
    for(i=0;i<n;i++)
        s+=*(p+i);
    return s;
}[/php]
It would be better to pass n into this function rather than depending on a global variable.  Also, why *(p+i) instead of p[i]?

> [php]
    if(sum(&check[0]) != n)
[/php]
[php]
        if(sum(&check[0]) == n)
[/php]

In other words, sum(check).

Also, getline isn't part of the C standard -- #include <getline.h> to use it with a conforming toolchain that supplies it.

---

### Post by c2tarun on 2010-12-18
> **saulgoode said:**
> Arrays are always passed by reference in C. This is because at compile time, the size of an array may not be known (whereas the size of structs, floats, ints, etc are fixed).

So when your 'func()' executes "check[c]=1", you are actually modifying main's local variable.
is there any was so that we can pass array by call by value??

---

### Post by Arndt on 2010-12-18
> **c2tarun said:**
> is there any was so that we can pass array by call by value??

You can put it inside a struct. But if it's large, this is not a good idea, since it is put on the stack, and stack space is not guaranteed to be very large.

I don't know what you want to do, but a usually better way is to make a copy and pass a pointer to the copy (or pass the original and let the callee do the copying, whichever is most suitable).

---

### Post by c2tarun on 2010-12-18
> **Arndt said:**
> You can put it inside a struct. But if it's large, this is not a good idea, since it is put on the stack, and stack space is not guaranteed to be very large.

I don't know what you want to do, but a usually better way is to make a copy and pass a pointer to the copy (or pass the original and let the callee do the copying, whichever is most suitable).


I think i'll let the callee do the copying :)

---

