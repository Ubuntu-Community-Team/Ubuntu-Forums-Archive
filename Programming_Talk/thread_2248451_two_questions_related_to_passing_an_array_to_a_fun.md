---
title: "two questions related to passing an array to a function in c"
date: 2014-10-14
forum: Programming Talk
---

### Post by IAMTubby on 2014-10-14
Hello,
 I have two questions related to passing an array to a function. Assume this is the code I have written
```
#include <stdio.h>

int a[] = {1,2,3,4,5,6};


int main(void)
{
 fun(a);
 //printf("in main, sizeof(a) == [%zu]\n",sizeof(a));


 return 0;
}


int fun(int a[])
{
 int i = 0;


 while(1)
 {
  if( (a+i) )
  {
   printf("%d ",*(a+i));
   i++;
  }
  else
   break;
 }
 //printf("in main, sizeof(a) == [%zu]\n",sizeof(a)); //I'm aware that this doesn't work because a here is a pointer and not an array, so sizeof(a) would always give me 8 on my 64-bit machine.
}

```

1. How do I find the number of elements in the array? I'm aware that I cannot do a sizeof(a) inside the function because a[] is actually a pointer.
2. To receive the array, ie, in the line int fun(**____**), which one would you suggest me? int fun(**int* a**){} or int fun(**int a[]**){} ?

Please advise.
Thanks.

---

### Post by spjackson on 2014-10-15
In answer to your first question, you have 2 choices both of which are used in various circumstances in C. These are:
[LIST=1]
[*]Use a sentinel value to indicate the end of the array.
[*]Pass the number of elements of the array as an additional parameter.
[/LIST]

An example of the first choice is a nul terminated C-string. Here the nul byte is the sentinel value - consider strcpy for example. Or you might have an array of pointers where the final element is NULL.

An example of the second choice would be strncpy, memcpy etc.

As far as the second question is concerned, both forms have the same meaning to the compiler, so ultimately it makes no difference. From a stylistic point of view, I have heard it argued that int a[] is better if you are expecting a pointer to the first element of an array and int * a is better if you are expecting a pointer to a single item. Here "better" means in terms of documentation for the programmer because, as I say, it makes no difference to the compiler. While I see some merit in this argument, those who advocate it tend in practice to make an exception for char * thereby undermining their argument. Personally, I prefer to use the pointer form and a meaningful identifier name: singular if you expect 1 and plural if you expect many.

---

### Post by ofnuts on 2014-10-15
> **spjackson said:**
> IAs far as the second question is concerned, both forms have the same meaning to the compiler

Hmm. Why is the sizeof operator making faces :)

---

### Post by IAMTubby on 2014-10-15
> **spjackson said:**
> In answer to your first question, you have 2 choices both of which are used in various circumstances in C. These are:
[LIST=1]
[*]Use a sentinel value to indicate the end of the array.
[/LIST]
Thanks spjackson
Just to clarify, if the array in question is an array of **integers** which are meant for sorting, say, and we have no idea of the input because any number could be given for sorting, won't this method be not-possible to implement?
Basically, I mean that, if no value can be regarded as a sentinel value.

---

### Post by ofnuts on 2014-10-16
> **IAMTubby said:**
> Thanks spjackson
Just to clarify, if the array in question is an array of **integers** which are meant for sorting, say, and we have no idea of the input because any number could be given for sorting, won't this method be not-possible to implement?
Basically, I mean that, if no value can be regarded as a sentinel value.

Yes, if no value is special, you can't use the sentinel value technique. One possible way is to use a struct with a "flexible array", one element of the struct being the size of the other element, the array. See [http://stackoverflow.com/questions/2060974/dynamic-array-in-struct-c](http://stackoverflow.com/questions/2060974/dynamic-array-in-struct-c). Thus way you can always tell how big the array is.

---

### Post by IAMTubby on 2014-10-17
> **ofnuts said:**
> Yes, if no value is special, you can't use the sentinel value technique. One possible way is to use a struct with a "flexible array", one element of the struct being the size of the other element, the array. See [http://stackoverflow.com/questions/2060974/dynamic-array-in-struct-c](http://stackoverflow.com/questions/2060974/dynamic-array-in-struct-c). Thus way you can always tell how big the array is.
Thanks ofnuts. I did go through the link you posted.

---

