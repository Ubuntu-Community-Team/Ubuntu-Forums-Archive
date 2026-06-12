---
title: "Strange memory issue"
date: 2012-02-28
forum: Programming Talk
---

### Post by Dirich on 2012-02-28
Hello,

I'm looking for a bit of brainstorming to help me in catching a nasty problem with my pointers.
I am trying to understand what could generate such behaviour, which in short is the following:

```

int main()
{
    double *a, *b, *c, *d;

    printf("a %p\nb %p\nc %p\nd %p\n", a, b, c, d);

    a = NULL;
    b = NULL;
    c = NULL;
    d = NULL;

    printf("a %p\nb %p\nc %p\nd %p\n", a, b, c, d);

STUFF
}

```

Note 1: I actually define many more variables together with a, b, c, d.
Note 2: STUFF is short for thousands of line of codes with function calls etc.

So what is startling me is that the result of the first printf is something like:
a 0xb6a1535c
b 0xc6a3245a
c 0xb6a1255a
d 0xc6a3441b

and the output from the second is:
a 0xb6a1535c
b (nil)
c 0xb6a1255a
d (nil)

In other words, at the very beginning of the program, after I print the values of a, b, c, d, I set all them to NULL and some of them do not "obey" the instruction.

Normally I would think of errors in the code, but what kind of error (which must occur AFTER the instruction, since it's at the very beginning) can induce such a behaviour?


The only thing I've found is that if I modify the inputs so that some more macro appear in the header I use to configure the program, then even d starts to ignore the d = NULL instruction.



Just to be clear, I'm suspecting that there is something different than the usual pointer problems in which I try to deallocate something not allocated or where I change the value of a pointer so that I lose track of the area of memory of interest and instead I try to operate on a random are who wasn't really allocated.
Any idea?

Thank you!

P.S.
I'm not posting the code because I'd like to solve the problem by myself, at least I'd like to try a bit more, but I'm at a loss against a problem that manifest itself before the "instruction that is causing the problem" is even run. :(

---

### Post by ofnuts on 2012-02-28
Optimizer bug? What happens if you do pointer arithmetic (a-b,c-d)? What happens if you initialize them when you declare them?

```

    double *a=NULL, *b=NULL, *c=NULL, *d=NULL;

```

---

### Post by Bachstelze on 2012-02-28
Can't reproduce with only the bit of code posted.

---

