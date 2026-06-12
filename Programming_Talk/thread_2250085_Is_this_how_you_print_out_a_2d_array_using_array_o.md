---
title: "Is this how you print out a 2d array using array of pointers?"
date: 2014-10-26
forum: Programming Talk
---

### Post by IAMTubby on 2014-10-26
Hello,
 Can you please give me an example on printing out the elements of a 2d array using an array of pointers. I'm looking to see how the array is defined inside main, how it is received by the receiving function, and then how the individual elements are accessed by the receiving function. I tried writing something. Is this right?

```

#include <stdio.h>


int i = 0;
int j = 0;


int main(void)
{
 int* a[2];
 int array[][3] = {{0,0,0},{1,1,1}};


 a[0] = &array[0][0];
 a[1] = &array[1][0];
 fun(a);


 return 0;
}


int fun(int* b[2])//two arrays
{
 for(i=0;i<2;i++)
 {
  printf("%p ",b[i]);


  for(j=0;j<3;j++)
  {
   printf("%d ",b[i][j]);
  }
  printf("\n");
 }
}

```

---

### Post by trent.josephsen on 2014-10-26
Looks fine to me.

One thing to remember is that these two declarations are exactly equivalent:
```
int fun(int *b[2])
int fun(int **b)
```

because you can't pass an array directly to a function, so the 2 has no effect. (For instance, [FONT=monospace]sizeof b[/FONT] won't give you the actual size of the array, just the size of the pointer.)

You declare fun() to return an int, but don't return anything from it, and don't do anything with the return value. Functions that don't return anything should be declared to return void. If you **compile with plenty of warnings enabled**, you'll be informed about mistakes like this.

Also, as I mentioned [and ofnuts also noted](http://ubuntuforums.org/showthread.php?p=13151875#post13151875) in one of your other threads, you should **declare the function before using it**, either by moving its definition to before main() or by inserting this line somewhere before the first time you use it:
```
void fun(int *b[2]);
```

---

### Post by ofnuts on 2014-10-26
> **trent.josephsen said:**
> Looks fine to me.

One thing to remember is that these two declarations are exactly equivalent:
```
int fun(int *b[2])
int fun(int **b)
```


No. Try these:

```

void printSize1(int (*a)[5]) {
    printf("int (*a)[5]: sizeof *a: %d\n",sizeof (*a));
}

void printSize2(int **a) {
    printf("int **a: sizeof *a: %d\n",sizeof(*a));
}

```

---

### Post by trent.josephsen on 2014-10-27
One of these things is not like the others...
```
void printSize1(int (*a)[5]);
void printSize2(int **a);
void printSize3(int *a[5]);
```
I was talking about the last two. You're talking about the first two.

---

### Post by Steven_Williams on 2014-10-27
I think he is trying to say that an array of pointers is different than a pointer to a pointer. As far as function definitions and declarations go, both are equivalent.

---

### Post by IAMTubby on 2014-10-27
> **trent.josephsen said:**
> Looks fine to me.
> **ofnuts said:**
> No. Try these:
trent.josephsen,ofnuts,
Thank you for the replies; but I would like to take some time before replying (late in the day today). Would like to try out few things.

> 
Also, as I mentioned [and ofnuts also noted]("http://ubuntuforums.org/showthread.php?p=13151875#post13151875") in one of your other threads, you should **declare the function before using it**, either by moving its definition to before main() or by inserting this line somewhere before the first time you use it:
```
void fun(int *b[2]);
```
Thank you so much for pointing out, shall not repeat these in future.

---

### Post by IAMTubby on 2014-10-27
> **trent.josephsen said:**
> 
One thing to remember is that these two declarations are exactly equivalent:
```
int fun(int *b[2])
int fun(int **b)
```

Thanks trent.josephsen, I understand that well now.

But in the code below(almost the same as the previous one posted),something I don't understand is we are passing **'a' which is basically &a[0]**, which means the **address of the first array** which holds {0,0,0}, but in the **function fun** which receives it, we are making **an array receive it**. I find this analogous to passing an integer value from main, and having an array receive it. How's this working? (*Had we been receiving in fun as int** b, I would've had no problems understanding)*
```

#include <stdio.h>


void fun(int* []);


int i = 0;
int j = 0;


int main(void)
{
 int* a[2];
 int array[][3] = {{0,0,0},{1,1,1}};


 a[0] = array[0];//array[0] == &array[0], name of the array is same as the address of the first element of the array; here name of the array is a[0], not a
 a[1] = array[1];
 fun(a);**//&a[0]**


 return 0;
}


void fun(**int* b[2])//two arrays**
{
 for(i=0;i<2;i++)
 {
  printf("%p ",b[i]);


  for(j=0;j<3;j++)
  {
   printf("%d ",b[i][j]);
  }
  printf("\n");
 }
}

```

---

### Post by IAMTubby on 2014-10-27
> **trent.josephsen said:**
> Looks fine to me.
> **Steven_Williams said:**
> I think he is trying to say that an array of pointers is different than a pointer to a pointer. As far as function definitions and declarations go, both are equivalent.
> **ofnuts said:**
> No. Try these:
This is a almost a continuation of my previous post(just above)
Actually thinking again, seems like this syntax is true for all arrays. I'm not able to understand what the syntax **[]** means while receiving the argument in the called function fun. Can someone explain the syntax **[]** to me? I mean, my question is, you are passing one address &a[0] and you're receiving it in an array int a[]?


```

main()
{
 int a[] = {1,2,3,4,5};


 fun(a);//passing &a[0]
}


int fun(int a[])
{
 
}

```

---

### Post by ofnuts on 2014-10-28
> **IAMTubby said:**
> This is a almost a continuation of my previous post(just above)
Actually thinking again, seems like this syntax is true for all arrays. I'm not able to understand what the syntax **[]** means while receiving the argument in the called function fun. Can someone explain the syntax **[]** to me? I mean, my question is, you are passing one address &a[0] and you're receiving it in an array int a[]?


```

main()
{
 int a[] = {1,2,3,4,5};


 fun(a);//passing &a[0]
}


int fun(int a[])
{
 
}

```

By definition, if A is an array, A and &A[0] are the same since the "value" of an array is by definition the address of its first element.

---

### Post by IAMTubby on 2014-10-28
> **ofnuts said:**
> By definition, if A is an array, A and &A[0] are the same since the "value" of an array is by definition the address of its first element.
Thanks ofnuts.
I understand that a and &a[0] are the same, but can you maybe explain wrt int fun(**int a[]**)? I'm confused because, to me, it looks like we are passing just one address(not an array, just one element) &a[0] from the main, and the array (int a[] is an array, not a pointer)is able to hold it.

As I said, I would've had no problems at all if it was like fun(a); and int fun(int* a){}. *(I also understand that int a[] and int* a) are the same*. But when I see a[], I expect a collection of elements to be passed and I start questioning how an element is received by a collection.

> the "value" of an array is by definition the address of its first element.
Or, do you want me to **not think in terms of an 'array' array**?

I understand this is more of a thought thing, as to how you interpret int a[]; would like to know how people interpret it.

PS : If the function fun is defined like int fun(int **a[10]**){}, then I get even more confused because a[10] is actually *(a+10), which means you're passing &a[0] to int *(a+10). What? :) Am I being too dumb? Just trying to understand the syntax...

---

### Post by ofnuts on 2014-10-28
Nope, int a[] is a fundamentally a pointer in that context. If it were a whole array, it would be a full copy, and so would have a different address. Print the value of a (as a pointer: %p) in caller and callee, you will see that it is the same.

---

### Post by IAMTubby on 2014-10-28
> **ofnuts said:**
> Nope, int a[] is a fundamentally a pointer in that context. If it were a whole array, it would be a full copy, and so would have a different address. Print the value of a (as a pointer: %p) in caller and callee, you will see that it is the same.
Thanks ofnuts.
But do you think this syntax which conveys different meaning as per the context is slightly messy/confusing, or is it just me?
Obviously, the people who came up with this really smart and there might be different things that prevented them from having an easier syntax, but it still is confusing?

---

### Post by ofnuts on 2014-10-28
> **IAMTubby said:**
> Thanks ofnuts.
But do you think this syntax which conveys different meaning as per the context is slightly messy/confusing, or is it just me?
Obviously, the people who came up with this really smart and there might be different things that prevented them from having an easier syntax, but it still is confusing?

It's just you:) Read a book about C, instead of experimenting. Get the big picture. It makes sense.

---

### Post by trent.josephsen on 2014-10-31
I've been sans-Internet for a few days, but I have a different answer to this:
> **IAMTubby said:**
> But do you think this syntax which conveys different meaning as per the context is slightly messy/confusing, or is it just me?
Obviously, the people who came up with this really smart and there might be different things that prevented them from having an easier syntax, but it still is confusing?
In fact, I agree. It's downright weird that "int a[10]" declares a as pointer-to-int when it's a function parameter, but array[10]-of-int otherwise. Even weirder is the fact that this "pointer decay" rule doesn't apply to structs, so you can pass an array by-value simply by wrapping it in a struct, which defeats the very principle (function calls don't cause arbitrarily large copies) that makes pointer-decay useful.

The fact that arrays decay into pointers at all -- that I'm not arguing with. It's pretty logical, really. (But keep the exceptions in mind: when it's the argument of sizeof or the & operator, an array name does not decay.) If I were to design C today, though, I'd make "int f(int a[10])" invalid syntax. As it is, I just don't write function prototypes like that.

At the end of the day, this is one of those historical curiosities you find in C. It wasn't designed all at once, and it wasn't standardized until it had been in use for many years, so once in a while you run into things that don't really make sense from a design perspective. (Another one is the fact that string literals are non-const -- "const" wasn't in the language to begin with, and when it was introduced, changing the type of string literals would have affected the compilation of working code. You can make string literals const by compiling with -Wwrite-strings.) C isn't a perfect language, but we like it anyway :)

---

### Post by IAMTubby on 2014-11-01
> **trent.josephsen said:**
> 
In fact, I agree. It's downright weird that "int a[10]" declares a as pointer-to-int when it's a function parameter, but array[10]-of-int otherwise.
Haha :D thanks trent.josephsen. Feel like I'm making progress.

> 
 If I were to design C today, though, I'd make "int f(int a[10])" invalid syntax. As it is, I just don't write function prototypes like that..
Absolutely! Would've been so good if int f(int a[10]) was invalid syntax, and all we needed was int* a.
How do you write your function prototypes?

> C isn't a perfect language, but we like it anyway :)
Absolutely, easy for me to complain. I too realize that C is amazing.

---

### Post by ofnuts on 2014-11-01
> **trent.josephsen said:**
> I've been sans-Internet for a few days, but I have a different answer to this:

In fact, I agree. It's downright weird that "int a[10]" declares a as pointer-to-int when it's a function parameter, but array[10]-of-int otherwise. Even weirder is the fact that this "pointer decay" rule doesn't apply to structs, so you can pass an array by-value simply by wrapping it in a struct, which defeats the very principle (function calls don't cause arbitrarily large copies) that makes pointer-decay useful.

The fact that arrays decay into pointers at all -- that I'm not arguing with. It's pretty logical, really. (But keep the exceptions in mind: when it's the argument of sizeof or the & operator, an array name does not decay.) If I were to design C today, though, I'd make "int f(int a[10])" invalid syntax. As it is, I just don't write function prototypes like that.

At the end of the day, this is one of those historical curiosities you find in C. It wasn't designed all at once, and it wasn't standardized until it had been in use for many years, so once in a while you run into things that don't really make sense from a design perspective. (Another one is the fact that string literals are non-const -- "const" wasn't in the language to begin with, and when it was introduced, changing the type of string literals would have affected the compilation of working code. You can make string literals const by compiling with -Wwrite-strings.) C isn't a perfect language, but we like it anyway :)
There is a fundamental difference between pointer an array that explains the behavior. An array variable is a pointer to a fixed memory area (which is the one established by the array variable declaration). As such it has a real sizeof() that represents the size of the memory area, and it cannot be assigned to (it is truly a constant and cannot be an "lvalue"(*)) When you use the array name in an expression it is converted to a pointer type (a pointer to the first element) with two exceptions: sizeof, and & (&A is the same value as the pointer you get when you use A). This also means that you see the array as an array only when you use the name it was declared with, which is only valid in the scope where it is declared. Everywhere else what you have can only be the array name converted to a pointer.

(*) Hmm... did I just say that avariable is a constant? Yes I did. But then they also introduced "const" for other uses...

---

### Post by trent.josephsen on 2014-11-01
In answer to this:
> **IAMTubby said:**
> How do you write your function prototypes?

If I have a function that takes a pointer, I declare it as taking a pointer, not an array. I might change my mind if for instance this:
```
int fn(int a[10])
{
    a[100] = 0; /* probably out of bounds */
}
```
could be caught at compile time, but that would break compatibility with older code and as far as I know there is no compiler that does so.

---

