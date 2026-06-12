---
title: "Java recursive problem"
date: 2005-05-02
forum: Programming Talk
---

### Post by KLineD on 2005-05-02
Hi everyone.

I've implemented a recursive function in Java for my Digital Control course.

The function to implement is the following:
```
output(n) = .5*input(n-1)+1.9*output(n-1)+.9*output(n-2)
```

input is another function that returns 0 when (n-1) < 0 or else returns 1.

I already implemented a recursive function that does this, but my teacher says it's not very efficient since if I have to get the value for n = 100 the program has to calculate every value up to 100.

My question is, can this be done in a non recursive way?? My teacher says that I have to take n (for example 100) and calculate the output for 99 and 98 and then sum everything and that's it, but I can't see how am I supposed to calculate for n=99 if I need to know the output for n=98 and 97... all the way down to 0 where I know what's the output.

Any help is very appreciated.

---

### Post by ltmon on 2005-05-02
I won't solve the problem for you  :-# , but it looks like a slightly complicated case of tail-recursion.

A simple example of removing tail-recursion would be:

int factorial(int n)
{
    if (n < 2) 
        return 1;
    return n*factorial(n-1);
}

which can be reduced to:

int factorial(int n)
{
   int f = 1;
   while (n > 1)
        f *= n--;
    return f;
}

I think you'll find that your case reduces in a similar manner.

The other common method of removing recursion is to use a stack which you basically pop values off and push them on again.  The idea is to simulate Java's stack of function calls in a local data structure, which is more efficient both speed and memory wise.  If you google for "quicksort recursion stack" you might find a page giving a classic example of this technique.  

I recommend the book "Algorithms in C" by Sedgewick for this kind of thing (if you can read C of course... you should be able to understand it if you are a Java programmer).

L.

---

### Post by jerome bettis on 2005-05-03
"Algorithms in C by Sedgewick "

yes!  excellent book it's got a high place on my shelf.

um just looking at there's infinite recursion.  where's the base case?  you're calling output(n - 2) for ever and ever.

in general recursion is very inefficent.  function call overhead aside, it's slower than an iterative approach.  using a stack like suggested is a good idea.  

rewriting this without a base case is impossible / a total waste of time, so i won't attempt.  you can easily rewrite it iteratively though, just give it some thought.  but real quick, you can eliminate the input function by using the ternary operator.  and since the second operand of that expression is known to be 0 or 1, just say 0 or 0.5.

```
public int output(int n)  {
    return (n - 1 < 0 ? 0 : 0.5) + 1.9 * output(n - 1) + 0.9 * output(n - 2);
}
```

---

