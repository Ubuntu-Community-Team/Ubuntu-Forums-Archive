---
title: "remembering values in recursion"
date: 2014-05-28
forum: Programming Talk
---

### Post by IAMTubby on 2014-05-28
I came up with the following question to post the question.
_Assume you have an array of positive integers and you have to subtract the elements of the array such that you get 0._
So if {5,3,2} are the elements of the array, the answers could be [5-3-2], [5-2-3], [3-3] and so on. (Let's not worry about using the same element twice etc, because that's not the purpose of the question)

I have written the following code and it tells me how many ways each element of the array can be made to 0. 
```
#include <stdio.h>

int a[] = {5,3,2};
int n = sizeof(a)/sizeof(a[0]);
int count = 0;


int main(void)
{
 int i = 0;


 for(i=0;i<n;i++,count=0)
 {
  /* I want to find for each element of the array */
  fun(a[i]);
  printf("number of ways of \"zero'ing\" [%d] using elements in the array == [%d]\n",a[i],count);
 }


 return 0;
}


int fun(int w)
{
 int i = 0;
 int ret = 0;


 if(w == 0)
  return 0;


 for(i=0;i<n;i++)
 {
  if(w-a[i] >= 0)
  {
   ret = fun(w-a[i]);
   if(ret == 0)
    count++;
  }
 }


}

```

The output is as follows
```
number of ways of "zero'ing" [5] using elements in the array == [3]
number of ways of "zero'ing" [3] using elements in the array == [1]
number of ways of "zero'ing" [2] using elements in the array == [1]

```

**However, I want to see the path which caused 5 to become 0, as in 5-3-2. How do I get the values at every step? Please can you tell me how this is generally done in recursion/DP.**
I have made an attempt and have attached the C file with comments, as I don't want to clutter the post too much. Following is the output of the attached C file.
```
5 0
5 2 0 
5 3 0 
number of ways of "zero'ing" [5] using elements in the array == [3]




3 0 
number of ways of "zero'ing" [3] using elements in the array == [1]




2 0 
number of ways of "zero'ing" [2] using elements in the array == [1]





```

Please advise.
Thanks

---

### Post by ofnuts on 2014-05-28
If its only for display, you pass an additional string in each call. You start with an empty string, and each level appends its information to it, prints it and passes it to the next level.

If it must be used for more functional purposes, you use a [stack]("http://en.wikipedia.org/wiki/Stack_%28abstract_data_type%29"), where each instance of the recursion pushes its information on entry and pops it on exit.

---

### Post by IAMTubby on 2014-05-29
> **ofnuts said:**
> If its only for display, you pass an additional string in each call. You start with an empty string, and each level appends its information to it, prints it and passes it to the next level.

If it must be used for more functional purposes, you use a [stack]("http://en.wikipedia.org/wiki/Stack_%28abstract_data_type%29"), where each instance of the recursion pushes its information on entry and pops it on exit.
ofnuts, sorry I was away for a day.
Let me think about this, try and implement it and get back to you.

Thank you.

---

