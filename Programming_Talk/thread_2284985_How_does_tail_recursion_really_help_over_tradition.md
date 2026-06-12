---
title: "How does tail recursion really help over traditional recursion"
date: 2015-07-02
forum: Programming Talk
---

### Post by IAMTubby on 2015-07-02
Hello,
 I was reading up about the difference between tail recursion and Traditional recursion and find it [mentioned]("http://blogs.msdn.com/b/chrsmith/archive/2008/08/07/understanding-tail-recursion.aspx") that "[COLOR=#333333][FONT=Segoe UI]Tail Recursion however is a form of recursion that doesn&#8217;t use any stack space, and thus is a way to use recursion safely.[/FONT][/COLOR]"'

I am struggling to understand how.

_Comparing finding factorial of a number using the Traditional and tail recursion_

_Traditional recursion_
```
/* traditional recursion */
fun(5);


int fun(int n)
{
 if(n == 0)
  return 1;


 return n * fun(n-1);
}
```

Here, the call stack would look like
5 * fact(4)
        |
       4 * fact(3)
               |
              3 * fact(2)
                      |
                    2 * fact(1)
                            1 * fact(0)
                                    |
                                   1
EDIT : I meant the pipes to be directly below the recursive calls, looks a bit different being plain text

_Taill recursion_
```
/* tail recursion */
fun(5,1)


int fun(int n, int sofar)
{
 int ret = 0;


 if(n == 0)
  return sofar;


 ret = fun(n-1,sofar*n);


 return ret;
}
```
However, even here, the variable 'sofar' would hold - 5,20,60,120,120 at different points.
**But once return is called from the base case which is recursive invocation #4, it still has to return 120 to recursive invocation #3, then to#2, #1 and back to main.**
So, I mean to say that the stack **is** used and everytime you return to the previous call, the variables at that point in time can be seen, which means it is being saved at each step.

Unless, the tail recursion was written like below, I am not being able to understand how it saves stack space.
```
/* tail recursion */
fun(5,1)


int fun(int n, int sofar)
{
 int ret = 0;


 if(n == 0)
  **return sofar back to main function, stop recursing back; just a one-shot return**


 ret = fun(n-1,sofar*n);


 return ret;
}
```


Please advise.
Thanks.

---

### Post by Vaphell on 2015-07-03
it's a matter of optimization. If you don't optimize, there are no benefits, eg python doesn't care about the tail recursion so it's a wash in its case. On the other hand in some languages tail recursion is recognized and optimized to get rid of the recursive calls, replacing them with a loop spinning within a single frame.

article you linked gives example 

> 
```
let factorial x =
    // Keep track of both x and an accumulator value (acc)
    let rec tailRecursiveFactorial x acc =
        if x <= 1 then 
            acc
        else 
            tailRecursiveFactorial (x - 1) (acc * x)
    tailRecursiveFactorial x 1
```

The compiled F# code, when viewed under Reflector and converted to C#, looks like this. Which is clearly not going to use up any stack space:

```
public static int tailRecursiveFactorial (int x, int acc)
{
    while (true)
    {
        int num = x;
        if (num <= 1)
        {
            return acc;
        }
        acc *= x;
        x--;
    }
}
```

looks like a run of the mill while loop to me.

---

