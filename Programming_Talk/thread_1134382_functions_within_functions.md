---
title: "functions within functions??"
date: 2009-04-23
forum: Programming Talk
---

### Post by ayastona on 2009-04-23
```
int main()
{

MyFunction();

return 0;
}

void MyFunction()
{
  void MySubFunction()
  {
  }
}
```

is it possible?

---

### Post by stroyan on 2009-04-23
C won't allow nested function definitions.
Pascal will allow it.

---

### Post by Npl on 2009-04-23
Not allowed in C or C++.
gcc allows it as extension tough (only for C, not for C++): [Nested Functions]("http://gcc.gnu.org/onlinedocs/gcc-4.4.0/gcc/Nested-Functions.html")

---

### Post by CptPicard on 2009-04-23
The gcc extension is really handy though, it makes writing callbacks with closure-like behaviour so much easier, not to mention safer...

---

### Post by eye208 on 2009-04-24
> **ayastona said:**
> is it possible?
No, but you can define local function objects. Unlike local functions, it is safe to pass function objects as callbacks because their state is separate from the surrounding function.

---

### Post by Arndt on 2009-04-24
> **stroyan said:**
> C won't allow nested function definitions.
Pascal will allow it.

Some others will too. I don't know by heart, but look up what Python, Ruby, Perl, Javascript, Java and PHP do.

---

### Post by Reiger on 2009-04-24
Anything which implements the lambda statement will do that: lambda calculus is theory behind a means of defining functions; each arbitrarily nested lambda statement is an anonymous function.

Also, in JavaScript functions are objects, and objects are functions. As a result passing functions around as well as nesting functions becomes trivial (altough you may get burnt for doing that on MSIE, there are/used-to-be memory leaks involved).

---

### Post by samjh on 2009-04-24
[http://en.wikipedia.org/wiki/Nested_function](http://en.wikipedia.org/wiki/Nested_function)

---

### Post by mmix on 2009-04-24
> **Npl said:**
> Not allowed in C or C++.
gcc allows it as extension tough (only for C, not for C++): [Nested Functions]("http://gcc.gnu.org/onlinedocs/gcc-4.4.0/gcc/Nested-Functions.html")

It will be changed.
svn://gcc.gnu.org/svn/gcc/branches/cxx0x-lambdas-branch
[http://gcc.gnu.org/projects/cxx0x.html#lambdas](http://gcc.gnu.org/projects/cxx0x.html#lambdas)

[http://gcc.gnu.org/wiki/MiddleEndLispTranslator](http://gcc.gnu.org/wiki/MiddleEndLispTranslator)

---

### Post by Npl on 2009-04-24
> **mmix said:**
> It will be changed.
svn://gcc.gnu.org/svn/gcc/branches/cxx0x-lambdas-branch
[http://gcc.gnu.org/projects/cxx0x.html#lambdas](http://gcc.gnu.org/projects/cxx0x.html#lambdas)

[http://gcc.gnu.org/wiki/MiddleEndLispTranslator](http://gcc.gnu.org/wiki/MiddleEndLispTranslator)lamba functions (function objects) arent nested functions.
Nested functions are simpler and more restricted.

---

### Post by nvteighen on 2009-04-24
gcc allows it but is non-standard.

Lambdas are actually something more than functions... They also set an environment that allows you to create new bindings. This is much clearer when using functional languages... if you just want to slip in a new variable in runtime, use a lambda.

---

