---
title: "Why do functions need parameters sometimes."
date: 2009-05-31
forum: Programming Talk
---

### Post by hoboy on 2009-05-31
why sometimes functions/methods methods takes parameters ?
and sometimes not.
what is the relation between functions and their parameters ?

---

### Post by simeon87 on 2009-05-31
A function/method needs parameters when the calculations done by the function/method depend on those values. A function/method without parameters simply needs to do some work but no values need to be given to the function/method to do its work. It's useful to have parameters when you want to use code again but then for different values.

---

### Post by NielsBhor on 2009-05-31
With a function, if you call the function and pass no arguments, the function will ignore the arguments. If you have a function(const char*, int *) and you call it using one argument such as function(a) instead of function(a,b) then just the a will pass and the function ignores the b. 

This is generally what the case is with functions.

---

### Post by hoboy on 2009-05-31
> **simeon87 said:**
> A function/method needs parameters when the calculations done by the function/method depend on those values. A function/method without parameters simply needs to do some work but no values need to be given to the function/method to do its work. It's useful to have parameters when you want to use code again but then for different values.

Thanks, you mean if I have a repetitive problem solution that should give back a result I should use function with parameter on that function.
maybe the question is how do I look at a problem then decide this one need to be solved with function/method with parameter.

---

### Post by hoboy on 2009-05-31
> **NielsBhor said:**
> With a function, if you call the function and pass no arguments, the function will ignore the arguments. If you have a function(const char*, int *) and you call it using one argument such as function(a) instead of function(a,b) then just the a will pass and the function ignores the b. 

This is generally what the case is with functions.

Do you think you can give me an example of everyday life situation when on will use function/method and the parameter ?
NielsBhor was a very very smart physicist.

---

### Post by lisati on 2009-05-31
I'll do my best to keep it simple.

A function WITH paramaters is useful in a program when you have some specific information you want the function to work with. You might even want to work out the value of foobar(a) in one part of a program and possibly foobar(b) in another part of a program.

Whether or not a function needs paramaters (and how many and what sort) depends on what kind of work you expect the function to do.

I'm not sufficiently experienced in OOP programming to comment on the method side of things.

---

### Post by NielsBhor on 2009-05-31
Yes. Niels Bhor is a very smart guy for his time. There are so many applications why you would need a function. For example, calculating the angle of triangles using the Law of Sines. 

```

int law_of_sines(int *a, int *b, int* c)
{
  // design your algorithm here 
}

```

Simple as that. Where a, b, c are the sides of the triangle.

---

### Post by simeon87 on 2009-05-31
> **hoboy said:**
> Thanks, you mean if I have a repetitive problem solution that should give back a result I should use function with parameter on that function.

Yes, that would make sense. If you want to perform the same calculations but with different input values, it makes sense to create a function for it and then call that function when needed.

> **hoboy said:**
> maybe the question is how do I look at a problem then decide this one need to be solved with function/method with parameter.

You will know soon enough :) When you find yourself writing the same thing but with just different values/variables, it's time to create a function for it. When you have more experience, you can also think of the problem in terms of multiple functions: you start with a basic function that calculates just a simple thing related to your problem. Then you write a function that uses that first function to calculate something else. This is called bottom-up programming.

For example, when you need to calculate the value of all buildings in a city, you could first write a function that calculates the value of a building. This is a function with a building as a parameter. Then, for each building in a city, you could call that function and sum the results and this would be the value of all buildings in the city.

---

### Post by hoboy on 2009-05-31
> **lisati said:**
> I'll do my best to keep it simple.

A function WITH paramaters is useful in a program when you have some specific information you want the function to work with. You might even want to work out the value of foobar(a) in one part of a program and possibly foobar(b) in another part of a program.

Whether or not a function needs paramaters (and how many and what sort) depends on what kind of work you expect the function to do.

I'm not sufficiently experienced in OOP programming to comment on the method side of things.

Thanks.

---

### Post by hoboy on 2009-05-31
> **NielsBhor said:**
> Yes. Niels Bhor is a very smart guy for his time. There are so many applications why you would need a function. For example, calculating the angle of triangles using the Law of Sines. 

```

int law_of_sines(int *a, int *b, int* c)
{
  // design your algorithm here 
}

```

Simple as that. Where a, b, c are the sides of the triangle.
Thanks I got the point.
Nils..... Han var dansker

---

### Post by CptPicard on 2009-05-31
> **hoboy said:**
> 
what is the relation between functions and their parameters ?

Well, consider the relationship between a mathematical function and their parameters. A function is essentially a parametrized value that depends on the parameters. In a computer program (unless it is so called pure-functional) you have the added complexity of there being external state to the function in the program... no-parameter functions (sometimes called procedures) typically operate on that external state, creating some state change that does *not* depend on any passed-in value.
 
EDIT: And to expand on that -- in the bad old days you really would do this by altering some global state first, then calling your procedure, and reading the global state again to figure out the changes if you need them. Having temporary, "local" parameter values passed as parameters is much more preferable for altering the behaviour of whatever code you have decided to extract into your function.

> **NielsBhor said:**
> If you have a function(const char*, int *) and you call it using one argument such as function(a) instead of function(a,b) then just the a will pass and the function ignores the b. 

No, it will be a compiler or runtime error. Unless you are working with languages that allow for partial application (the result is then a new function), or default values (then the value will be the default value.


> **lisati said:**
> 
I'm not sufficiently experienced in OOP programming to comment on the method side of things.

OOP is mostly about two things -- an "inheritance hierarchy" on data items, plus some so-called dispatching mechanism to choose the correct function (method) for some given type of data item. Parametrization does not really factor much into this, except when considering that there is a so called implicit "self/this" pointer to the data item passed as a parameter to the method. Some languages such as Java and C++ hide it, some language such as Python make it explicit.

> **NielsBhor said:**
> Yes. Niels Bhor is a very smart guy for his time.

And his name was spelled "Bohr".. :)

---

### Post by NielsBhor on 2009-05-31
Nope. According to C++ HOW TO PROGRAM - FIFTH EDITION - by Deitel, you may have a function with arguments such a function (a,b). If you declare the function to be an int it must return an int regardless what is passed into the function. If you pass an a, the b gets dropped. But, you cannot pass the b and expect a to get dropped.

---

### Post by nvteighen on 2009-05-31
> **NielsBhor said:**
> Nope. According to C++ HOW TO PROGRAM - FIFTH EDITION - by Deitel, you may have a function with arguments such a function (a,b). If you declare the function to be an int it must return an int regardless what is passed into the function. If you pass an a, the b gets dropped. But, you cannot pass the b and expect a to get dropped.
The compiler will scream if you try that.

```

int myfunc(int, int);

int myfunc(int a, int b)
{
    return a + b; // Let's keep this simple
}

int main(void)
{
    int res = myfunc(3); // ???

    return res;
}

```

Here's g++'s scream:
```

ugi@UGI:~/Desktop$ g++ a.cpp -Wall
a.cpp: In function &#8216;int main()&#8217;:
a.cpp:3: error: too few arguments to function &#8216;int myfunc(int, int)&#8217;
a.cpp:10: error: at this point in file

```

---

### Post by NielsBhor on 2009-05-31
Ok. I'm going to send this over to the publisher.

---

### Post by CptPicard on 2009-05-31
gcc:

```

#include <stdio.h>

int testfunction(int a, int b) {
  return 1;
}

int main() {
  printf("%i", testfunction(5));
}

```

Result:

```

foo.c: In function &#8216;main&#8217;:
foo.c:11: error: too few arguments to function &#8216;testfunction&#8217;

```

This sort of stuff really should never work if there is no default value provided (like you can do in C++). The value would be undefined, so therefore it is obviously an error not to provide one.

(Congrats nvteighen for 2k posts...)

---

