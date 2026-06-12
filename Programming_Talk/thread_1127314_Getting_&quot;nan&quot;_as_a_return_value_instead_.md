---
title: "Getting &quot;nan&quot; as a return value instead of float in c++"
date: 2009-04-16
forum: Programming Talk
---

### Post by uast23 on 2009-04-16
Hi,

I am trying to return a float value from a function which is part of a library, written in c++, but whenever I call this function, I get the return value as nan instead  of float. Ubuntu version is 8.04, gcc is 4.2.3. Surprisingly, the same code works perfect in Fedora.  Any Inputs?? 

Don't bother about the code bcos its happening even with the simplest possible code.

---

### Post by Arndt on 2009-04-16
> **uast23 said:**
> Hi,

I am trying to return a float value from a function which is part of a library, written in c++, but whenever I call this function, I get the return value as nan instead  of float. Ubuntu version is 8.04, gcc is 4.2.3. Surprisingly, the same code works perfect in Fedora.  Any Inputs?? 

Don't bother about the code bcos its happening even with the simplest possible code.

Like what? sin(0.0) returns NaN?

---

### Post by uast23 on 2009-04-16
> **Arndt said:**
> Like what? sin(0.0) returns NaN?

sample is Like...

float foo()
{
   float ret = 23.33453 + 34.4546;
   return ret;
}

int main()
{
   float cap = foo();
   return 0;
}

here if i try to print cap, it shows nan.

actually the function is defined in a class inside a library.. am creating the object of that class and calling the function in main...

---

### Post by c174 on 2009-04-16
Did you recompile the library on your new platform?

How do you print the value? (using printf with a wrong format string can give strange results)

---

### Post by PaulM1985 on 2009-04-16
nan generally means Not A Number and is commonly down to dividing by zero.  It can also be created by things such as calculating the root of a negative number or the inverse sin or cos out of the range of -1, 1. etc.

I would really check the code and make sure this type of thing isn't happening.

Paul

---

### Post by nvteighen on 2009-04-16
Just a wild guess, but are you sure your processors are of the same kind? I mean, that both are 32-bit or both 64-bit...? And, of course, check for any non-portable code.

---

### Post by stevescripts on 2009-04-16
uast23 - if this is your library, I would suggest re-writing it to use type double, rather than float - floats are rather notorious for their lack of precision.

---

### Post by monkeyking on 2009-04-16
> **stevescripts said:**
> uast23 - if this is your library, I would suggest re-writing it to use type double, rather than float - floats are rather notorious for their lack of precision.

If 7.3 decs of precision is enough,
then stay with it.

---

### Post by dwhitney67 on 2009-04-16
> **uast23 said:**
> ...

here if i try to print cap, it shows nan.

...

Please show how you are attempting to print 'cap'.  Or is the problem deeper?  Show us your code!  Your example is too trivial to comment on.

---

### Post by uast23 on 2009-04-20
> **dwhitney67 said:**
> Please show how you are attempting to print 'cap'.  Or is the problem deeper?  Show us your code!  Your example is too trivial to comment on.

Thanks fr the responses....

Sad enuf... i have tried most of the things suggested here.. like  using double... 
explicitly casting return to float...
putting proper checks for Divide by zero everywhere...
writing the values into a file instead of printing...
both the processors are 32 bit...

till now nothing is working... 

am yet to recompile the library on the "erroneous" machine... trying the same...

---

### Post by Arndt on 2009-04-20
> **uast23 said:**
> Thanks fr the responses....

Sad enuf... i have tried most of the things suggested here.. like  using double... 
explicitly casting return to float...
putting proper checks for Divide by zero everywhere...
writing the values into a file instead of printing...
both the processors are 32 bit...

till now nothing is working... 

am yet to recompile the library on the "erroneous" machine... trying the same...

To be able to help, we seem to need a complete example: code, which when compiled and linked, behaves differently on the two systems. Is it the identical binary code (not recompiled), or do you build from source in both places?

Somewhere around here I would start using a machine level debugger (gdb can do that) to see exactly where the discrepancy arises, but knowing enough detail, maybe someone with more experience of floating point can offer a theory. Do other floating point applications work as they should? Other languages, python, perl, php?

---

