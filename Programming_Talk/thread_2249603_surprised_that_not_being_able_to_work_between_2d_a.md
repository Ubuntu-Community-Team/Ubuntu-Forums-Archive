---
title: "surprised that not being able to work between 2d arrays and pointers interchangeably"
date: 2014-10-23
forum: Programming Talk
---

### Post by IAMTubby on 2014-10-23
Hello,
 Say I pass a two dimensional array to a function and receive it in the function definition, as either int* a or int a[][colsize]. I'm surprised that inside the function I cannot access it using both pointers and the normal array notation immaterial of how it was received by the function definition. Surprised because arrays are basically designed using pointers(jumping above memory locations intelligently) and I would have expected both to work because a[i][j] is basically *(a+i*colsize+j). Let me give an example

_1.Receiving the array in the function definition using the array notation and trying to access elements using pointers_
```

#include <stdio.h>

int i = 0;
int j = 0;

int main(void)
{
 int a[2][5] = {
              {1,2,3,4,5},
              {6,7,8,9,10},
             };
 print(a);

 return 0;
}

int print(**int a[][5]**)
{
 for(i=0;i<2;i++)
 {
  for(j=0;j<5;j++)
  {
   //printf("%d ",a[i][j]); This obviously works, but the one below does not work
   **printf("%d ",*(a+i*5+j));** //Does not work
  }
  printf("\n");
 }
}

```

_Output_
Gives me a warning : warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;int *&#8217; [-Wformat] and random output when I run it.

_2.Receiving the array in the function definition using the pointer notation and trying to access using elements array notation_
```

#include <stdio.h>

int i = 0;
int j = 0;

int main(void)
{
 int a[2][5] = {
              {1,2,3,4,5},
              {6,7,8,9,10},
             };

 print(a);

 return 0;
}


int print(**int* a**)
{
 for(i=0;i<2;i++)
 {
  for(j=0;j<5;j++)
  {
   //printf("%d ",*(a+i*5+j)); This works, but why doesn't the notation below work? Aren't they the same thing?
   **printf("%d ",a[i][j]); //**Does not work
  }
  printf("\n");
 }
}

```

_Output_
error: subscripted value is neither array nor pointer nor vector



_Works for oned arrays_
I'm surprised because the same experiment works for one dimensional arrays and I'm able to use the notations interchangeably. See example below, both of these work
_3.Receiving the array in the function definition using the array notation and trying to access using elements pointer notation_. This works.
```

#include <stdio.h>

int i = 0;

int main(void)
{
 int a[] = {1,2,3,4,5};

 print(a);

 return 0;
}

int print(**int a[]**)
{
 for(i=0;i<10;i++)
  **printf("%d ",*(a+i)); **//Works fine
}

```

_4.Receiving the array in the function definition using the pointer notation and trying to access using elements array notation_. This also works
```

#include <stdio.h>

int i = 0;

int main(void)
{
 int a[] = {1,2,3,4,5};

 print(a);

 return 0;
}

int print(**int* a**)
{
 for(i=0;i<10;i++)
  printf("%d ",**a[i]**);//Works fine
}

```


Please advise as to why 1 and 2(above) don't work.
Thanks.

---

### Post by Rocket2DMn on 2014-10-23
The reason behind these not working comes down to an understanding in how C either passes arrays by *value* (not a pointer) or by *reference* (pointer).  In the first case, you are passing the array by value, so the entire array is copied when it's passed to the print function.  Therefore, you can't update its values and have the results reflected in the main function.  You can still print using pointers though, but you have to start at "a[0][0]", not just "a":
```

printf("%d ", *(&a[0][0]+i*5+j));

```

In the second case, you're passing a pointer.  Since the function doesn't know the column size, it can't properly set the offset the first [] (in this case, 5*sizeof(int)).  In cases 3 and 4, no such offset is needed, so as long as the code knows it's an int, it can jump to the correct location in memory (since it knows sizeof(int)).

---

### Post by Steven_Williams on 2014-10-23
Your problem with 1 is you are only dereferencing it once. To access it like you intend you need to do the following:
```
printf("%d ", *(*(a+i)+j));
```

Your problem with 2 is you are specifying just a pointer rather than a pointer to a pointer. You need it to be a pointer to a pointer so you can dereference the second array; otherwise, it will complain about getting a pointer to int because that is what you are giving it.

---

### Post by 3246251196 on 2014-10-23
The best way to deal with these problems - for me, at least - it to draw a picture.


```

|1|2|3|4|5|   |6|7|8|9|10| // [5]
 ^            ^
 |            |
 |            |
|ptr1        |ptr2        | // [2]
```

You  know that the value in memory "cubby-hole" is just an address to  another contiguous block of memory which stores 5 elements. That is, the  value of ptr1 is the address of the block containing values 1-5. We want to  dereference the address of ptr1 because the value (brought about by the  dereferencing) is a pointer to the block of 5 values. So, we can slowly  build it up: *(a+i) // the addr of "what we want". Now we need to  dereference that address to get the values: *(*(a+i)) , not forgetting  to incremement by j to move along as the loop goes: *(*(a+i)+j)

This  may seem unhelpful as the answers are already given. My point is that I  find it helpful to go back to good old pen and paper just to prove  things and understand them. Perhaps other people may find this approach  useful.

---

### Post by trent.josephsen on 2014-10-24
> **Rocket2DMn said:**
> The reason behind these not working comes down to an understanding in how C either passes arrays by *value* (not a pointer) or by *reference* (pointer).  In the first case, you are passing the array by value, so the entire array is copied when it's passed to the print function <snip>

This is not true; C will never implicitly copy an array. The issue here is a question of what type the pointer is.

In the following case,
```
int print(int a[][5]);
```
you declare print as taking a **pointer to array[5] of int**. In that context, (a+i*5+j) is also of type **pointer to array[5] of int**, and when you dereference it, you get a value of type **array[5] of int**, which, [since this is not one of the three exceptional cases, decays](http://c-faq.com/aryptr/aryptrequiv.html) into **pointer to int**. That's why you get a warning about passing pointer-to-int to printf() when it is expecting int.

This is where some people might think the type is the problem, and that they could get the right value by converting the pointer to the right type with a cast before dereferencing it: *(int *)(*(a+i*5+j)). But that would be a big mistake: the pointer you get in that case is not even pointing at the right location! Pointer arithmetic is done with respect to the size of the pointed-to type, so when the pointer is a pointer-to-array[5]-of-int, adding N to the pointer increments it by N *times the size of array[5]-of-int*. I mention this because the type error was the first hint that you were making a mistake. If you had silenced that error with a cast, as people often want to do, you might not have any idea that the indexing was all wrong. You didn't do that, and so I congratulate you on not falling into this trap. Keep this in mind: don't use casts to silence type errors, fix the type errors.

Steven_Williams has a solution that fixes that problem, but I'd like to point out (no pun intended) that there is a **huge** difference between "a pointer to a pointer" and "a pointer to an array" in a construct like *(*(a+i)+j). When a is of type pointer-to-pointer-to-int, *(*(a+i)+j) suggests that a points to an **[array of pointer to int]("http://c-faq.com/aryptr/dynmuldimary.html")**, which is very different from the **pointer to array of int** you actually have. [The differences between arrays and pointers go beyond just their types.](http://c-faq.com/aryptr/aryptr2.html)

In the second case, if you had warnings turned on, you should have gotten one about the implicit declaration of the `print' function. Because you didn't declare print before using it, like this:
```
    int print(int *);
```
(either inside or outside main), you missed out on another warning that would have given you another clue to the problem in that code:
```
foobar.c: In function ‘main’:
foobar.c:14:8: warning: passing argument 1 of ‘print’ from incompatible pointer type
  print(a);
        ^
foobar.c:13:6: note: expected ‘int *’ but argument is of type ‘int (*)[5]’
  int print(int *);
      ^
```

In other words, you defined a function that takes a pointer-to-int, and passed it a pointer-to-array[5]-of-int. Although [the pointer's *value* is the same](http://c-faq.com/aryptr/aryvsadr.html), the *type* mismatch is an important clue to how these two cases work differently, and why you can't treat them as the same. (Compile with at least "-std=c11 -Wall -Wextra" to be warned about these and many other classes of errors.)

**tl;dr** No, a[i*N + j] *is never the same* as a[i][j]. **BUT**, if a and b are defined like this:
```
int a[M*N];
int b[M][N];
```
Then a[i*N + j] *does essentially the same thing* as b[i][j]. The i*N + j thing is basically [a trick to pretend you have a two-dimensional array when all you have is a one-dimensional one](http://c-faq.com/aryptr/ary2dfunc2.html). There's no reason to do such gymnastics when you actually have a two-dimensional array -- that is, when N is known at compile time.

I'll happily ramble on if you have followup questions, but I also agree with what Steven_Williams said in [another thread](http://ubuntuforums.org/showthread.php?t=2249593&p=13150691#post13150691): You can't effectively learn C by experimentation. I don't know if you have a book -- we have book threads around here on a semi-regular basis, so you ought to be able to find some useful information by searching. Also, I may have mentioned this before, but you will learn a lot about C by lurking in comp.lang.c and posting questions on Stack Overflow (you can post in comp.lang.c, but I suggest not without your flame-retardant underwear). C is complex and a lot of people are willing to help out, but you have to know where to go.

---

### Post by IAMTubby on 2014-10-25
> **Steven_Williams said:**
> 
Your problem with 2 is you are specifying just a pointer rather than a pointer to a pointer. You need it to be a pointer to a pointer so you can dereference the second array; otherwise, it will complain about getting a pointer to int because that is what you are giving it.

> **trent.josephsen said:**
> 
you defined a function that takes a pointer-to-int, and passed it a pointer-to-array[5]-of-int. Although [the pointer's *value* is the same]("http://c-faq.com/aryptr/aryvsadr.html"), the *type* mismatch is an important clue to how these two cases work differently, and why you can't treat them as the same.

The i*N + j thing is basically [a trick to pretend you have a two-dimensional array when all you have is a one-dimensional one]("http://c-faq.com/aryptr/ary2dfunc2.html"). There's no reason to do such gymnastics when you actually have a two-dimensional array -- that is, when N is known at compile time.


Steven_Williams, trent.josephsen
I clearly understand what both of you say, thank you so much. I have been trying to get it to work based on the explanation above and my new understanding that I should receive it as a pointer to pointer.
I tried with this change, but not there yet. Where am I going wrong?
```

#include <stdio.h>


int i = 0;
int j = 0;


int main(void)
{
 int a[2][5] = {
              {1,2,3,4,5},
              {6,7,8,9,10},
             };


 print(a);


 return 0;
}


int print(**int** a**)//Made this change
{
 for(i=0;i<2;i++)
 {
  for(j=0;j<5;j++)
  {
   [B]//printf("%d ",a[i][j]);/Does not work
   printf("%d ",*(*(a+i)+j));//Does not work[/B]
  }
  printf("\n");
 }
}

```

PS : I have been able to get the first one to work based on the change you two suggested : *(*(a+i)+j). I still haven't got the "decaying to pointer to int" part though. Let me do some reading up and come back after some time.

---

### Post by ofnuts on 2014-10-25
Array notation works in "print()" if you declare the parameter properly (note that normally you should declare the function before using it...):

```

#include <stdio.h>

int i = 0;
int j = 0;

void print(int (*a)[5]) 
{
 printf("Print: a at %p, a[0]=%p, a[1]=%p\n",a,a[0],a[1]);
 for(i=0;i<2;i++)
 {
  for(j=0;j<5;j++)
  {
   printf("%d ",a[i][j]);
  }
  printf("\n");
 }
}

int main(void)
{
 int a[2][5] = {
              {1,2,3,4,5},
              {6,7,8,9,10},
             };
 printf("Main: a at %p, a[0]=%p, a[1]=%p\n",a,a[0],a[1]);
 print(a);

 return 0;
}

```

See the explanation [here](http://c-faq.com/aryptr/pass2dary.html)

---

### Post by IAMTubby on 2014-10-25
> **ofnuts said:**
> Array notation works in "print()" if you declare the parameter properly (note that normally you should declare the function before using it...):

```

#include <stdio.h>

int i = 0;
int j = 0;

void print(int (*a)[5]) 
{
 printf("Print: a at %p, a[0]=%p, a[1]=%p\n",a,a[0],a[1]);
 for(i=0;i<2;i++)
 {
  for(j=0;j<5;j++)
  {
   printf("%d ",a[i][j]);
  }
  printf("\n");
 }
}

int main(void)
{
 int a[2][5] = {
              {1,2,3,4,5},
              {6,7,8,9,10},
             };
 printf("Main: a at %p, a[0]=%p, a[1]=%p\n",a,a[0],a[1]);
 print(a);

 return 0;
}

```

See the explanation [here]("http://c-faq.com/aryptr/pass2dary.html")
ofnuts, I went through the link you gave me and it fits in  perfectly with my question. I also understood your example and the one given in the link. So 'a' is basically a pointer to an _array that holds 5 ints_. just underlining it because I like to read these words in one shot(makes it easy for me to visualize)
 
I have a couple of questions:
1.I'm kind of feeling disappointed reading this line from the link you gave me, **"An array of arrays (i.e. a two-dimensional array in C) decays into a pointer to an array, not a pointer to a pointer".** I mean, is there any reason to that?
Passing a two-d array and receiving it as int** p; is perfectly correct, I feel, meaning wise. Why is it that the array decays into a pointer to an array?

2.When I receive a one dimensional array inside a function like

```
main()
{
 int myarray[] = {1,2,3,4,5};
 fun(myarray);
}

int fun(int a[])
{

}
```
What does that notation int a[] actually mean? myarray means &myarray[0] which means the address of the first element, not able to understand what int a[] means.

---

