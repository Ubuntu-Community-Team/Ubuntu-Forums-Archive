---
title: "Passing a function and its arguments"
date: 2009-01-22
forum: Programming Talk
---

### Post by dosh on 2009-01-22
I know how to pass a function via a pointer to another function but is there a way to pass its arguments with it. And if so can it be a variable argument list. 

I notice in g_connect_signal that you give it the function name to call on the signal but you are not giving it that number of arguments, but a pointer to the data. So at somepoint in the g code it is converting the pointer to its arguments and sending that number of arguments to the function requested. I am wondering how this is done.

Hopefully this makes sense.

---

### Post by CptPicard on 2009-01-22
Well, I did something like that here

[http://www.voittoporukka.fi/~eero/c-analyzer/analyzer.c](http://www.voittoporukka.fi/~eero/c-analyzer/analyzer.c)

a while ago. Look at the "callback" function passing and the void** argument list. It's pretty unsafe but works.

Also, you can use the gcc extensions for nested functions to get closure-like behaviour...

---

### Post by jmartrican on 2009-01-22
Have you looked at bind or boost::bind?  Its used a lot in boost::asio for callbacks.

There are ways around this.  For example you can just pass an object or ref to an object.  The object can be a functor or have a member function.

---

