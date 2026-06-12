---
title: "Can't understand this one line of code in merge sort - trouble with pointers"
date: 2014-10-20
forum: Programming Talk
---

### Post by IAMTubby on 2014-10-20
Hello,
 I've been trying to understand this particular part of merge sort for few days, and finally think that I need some advice. 
As mentioned in the comments below, **merge(A1, n1, A2, n2, A);** combines sorted arrays A1 and A2 into A. I understand merge sort well, but I'm _not able to understand how the combined sorted array A copies it's values to A1 or A2_ depending on who called it _when it goes back to the previous invocation of the recursive function._

Let me explain with an example, Say the initial array was : {3,1,2,6,4,7,5,8}
_At some step : _
A1 : {1,3},
A2 : {2,6}
now call merge(A1,A2,A). This will give
A : {1,2,3,6}
So far so good, but now when it goes back to the previous invocation after doing the two frees,
**A1 : {1,2,3,6}**
A2 : {4,7,5,8} 
**How does A1 get these values? I'm confused because, I feel A has already copied it's values to A1 and A2 before calling merge, which means, any changes in A will not be reflected in A1 and A2?**

I would like to understand how, A1 in (i-1)th recursive invocation, gets the values in A in the ith invocation
*I think it's something to do with merge_sort(**int *A**, int n)* or something, but please can you elaborate a bit further.
                    
```
int merge_sort(int *A, int n)
{
  int i;
  int *A1, *A2;
  int n1, n2;


  if (n < 2)
    return;   /* the array is sorted when n=1.*/


  /* divide A into two array A1 and A2 */
  n1 = n / 2;   /* the number of elements in A1 */
  n2 = n - n1;  /* the number of elements in A2 */
  A1 = (int*)malloc(sizeof(int) * n1);
  A2 = (int*)malloc(sizeof(int) * n2);


  /* move the first n/2 elements to A1 */
  for (i =0; i < n1; i++) {
    A1[i] = A[i];
  }
  /* move the rest to A2 */
  for (i = 0; i < n2; i++) {
    A2[i] = A[i+n1];
  }
  /* recursive call */
  merge_sort(A1, n1);
  merge_sort(A2, n2);


  /* conquer */
  merge(A1, n1, A2, n2, A); //**assume this function merges the two sorted arrays A1 and A2 into A**
  free(A1);
  free(A2);
}

```

PS : I have also attached the entire code in case this code snippet is not sufficient.

---

### Post by ofnuts on 2014-10-20
What happens is:


[LIST]
[*]The function splits A into A1 and A2,
[*]Then it calls itself recursively on both A1 and A2
[*]So after the two calls to merge_sort(), A1 and A2 are assumed sorted.
[*]Then it calls merge(A1, n1, A2, n2, A) to fill A with the ordered values in A1 and A2, so A now contains the initial data, sorted.
[*]Due to the recursive usage of merge_sort(), A1 at the upper level is A at the level under (same pointer value, just different variable names for it)
[/LIST]

---

### Post by IAMTubby on 2014-10-21
> **ofnuts said:**
> What happens is:
[LIST]
[*]Due to the recursive usage of merge_sort(), A1 at the upper level is A at the level under (same pointer value, just different variable names for it)
[/LIST]

Thanks a lot ofnuts for the reply. merge_sort(A1, n1); calls int merge_sort(int *A, int n). I don't know how I missed that, for three days at a stretch :)

---

### Post by IAMTubby on 2014-10-21
> **ofnuts said:**
> What happens is:


[LIST]
[*]The function splits A into A1 and A2,
[*]Then it calls itself recursively on both A1 and A2
[*]So after the two calls to merge_sort(), A1 and A2 are assumed sorted.
[*]Then it calls merge(A1, n1, A2, n2, A) to fill A with the ordered values in A1 and A2, so A now contains the initial data, sorted.
[*]Due to the recursive usage of merge_sort(), A1 at the upper level is A at the level under (same pointer value, just different variable names for it)
[/LIST]


> **IAMTubby said:**
> I'm _not able to understand how the combined sorted array A copies it's values to A1 or A2_ depending on who called it _when it goes back to the previous invocation of the recursive function._
For the benefit of future readers,
I spent some more time thinking as to why I did not get this before ofnuts helped me out with the last line in his reply. It's because this code has call-by-reference on variables inside a recursive function.
Please find my comments below, which is like a summary of my understanding, and might help someone reading this.
```

/* visualize this as similar to */
/*
   somefun()//actually somefun is ith invocation of divide and the divide you see below is i+1 or 1 level deeper invocation of divide
   {
_____ \   divide(**A1**,n/2);
      /
|  }
| 
|  divide(**int* a,** int n)//Which means, A1 from somefun is actually 'a' in divide
|  {
|         //do all the logic on 'a'
|  
|         //store sorted array in a(the sort is done by the conquer step, but it's part of 'all the logic'. So logic is basically three steps you could say - merge,merge,conque    
|          a;
|  }       |
|__________|//When this divide function finishes all operations and returns to the function which called it - somefun(which in this case is the previous invocation of the same function), it is received with all it's updated contents(because we're doing call-by-reference) in the name in which it was called from the i+1th instance, here the label is A1. So basically it's recursion + call/receive by reference. Phew!

```

Normally, If I'm doing call-by-reference on a variable, I would prefer to give the same name(label) to the variable in the calling function as well as the called function, like below, just for a visual cue, that, hey, this is the same variable. I know it doesn't matter because we're operating directly on addresses(memory) and so the name doesn't matter.
```

main()
{
 int* a;
 a = malloc(5 * sizeof(int));

*a = 3;
*(a+1) = 2;
*(a+2) = 1;
*(a+3) = 4;
*(a+4) = 5;

 fun(a);
}

int fun(int* a)
{
 //access the array here
}

```

Thanks ofnuts, once again.

---

