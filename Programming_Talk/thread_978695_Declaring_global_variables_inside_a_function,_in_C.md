---
title: "Declaring global variables inside a function, in C?"
date: 2008-11-11
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-11
This is a very dumb question but haven't still found answer.

---

### Post by dexter on 2008-11-11
Declare them static, e.g.
```

static int i;

```

What exactly is your purpose?

---

### Post by dwhitney67 on 2008-11-11
Not a dumb question at all.

The answer is that it cannot be done.  The variable will only have scope within the function.

Global variables must be declared outside of a function scope (and before you think otherwise, main() is a function too).  Globals are declared within header files or within .c modules.

P.S.  I should point out that when developing a project with multiple .c modules, one of them must instantiate the global variable; the other(s) must declare it as an "extern" variable.  Otherwise if two or more modules each have their own instantiations of the variable, the compiler will not be happy with that.

---

### Post by snikrot on 2008-11-11
Why do you wish to declare a global variable inside a function. The variable wouldn't be known to other functions.

See also [http://www.cplusplus.com/doc/tutorial/variables.html]("http://www.cplusplus.com/doc/tutorial/variables.html")

It would be easier to declare the variable outside the function and give it a value inside it. Or even better take a pointer outside the function with the value NULL and inside the function set it to the correct value.

---

### Post by crazyfuturamanoob on 2008-11-11
I wanted to have an initializition function which declares some variables and makes them global, because I thought it's one keyword which makes them global.

Doesn't matter me much. Thanks.

---

### Post by LaRoza on 2008-11-11
> **crazyfuturamanoob said:**
> I wanted to have an initializition function which declares some variables and makes them global, because I thought it's one keyword which makes them global.

Doesn't matter me much. Thanks.

You could declare the variables as global, then use a function to give them a value.

---

