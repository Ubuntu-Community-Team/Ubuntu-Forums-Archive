---
title: "Fastest Paradigm"
date: 2008-06-12
forum: Programming Talk
---

### Post by Sinkingships7 on 2008-06-12
Just a quick and (hopefully) simple question that I can't seem to find the answer to anywhere else:

Which is faster - sending messages to objects, or calling functions?

If the answer depends on the language, I'm currently pretty far in my studies with C++, so this is the language of which I'm specifically referring to. 

Perhaps an example?

Say I wanted to find out the length of a string. Let's also say that I have a pre-written class that defines various string manipulation functions, one of which is to find the length of a string with a method called "string_length".

Which way is faster:

a.) my_string_length = strlen(my_string);
OR
b.) my_string_length = string_object.string_length(my_string);

For you picky people out there, I'm referring to execution time, not speed of development.

---

### Post by slavik on 2008-06-12
OO is pretty much what is called syntactic sugar.

OO:
string str = "hello";
int length = str.length();

C-like:
char str[] = "hello";
int length = strlen(str);

the above will be executed at the same speed. OO gives a performance penalty when the only way to know for sure when to call a method is during run-time. in other words, when you have a class inheriting some other class but it caries a pointer of the class it inherited from.

---

### Post by mike_g on 2008-06-12
Well with both a and b you are calling a function. Any difference in speed would be mainly down to how the different functions work internally. The standard functions (IE: strlen in C) tend to be very fast.

If you have your own string class, you could add a variable that holds the string length and only update it when the string changes.  If the custom function does nothing more than get a variable it should be faster then calling strlen().

If its important you could always run both functions several million times and see what comes out faster.

---

### Post by Sinkingships7 on 2008-06-12
> **mike_g said:**
> If its important you could always run both functions several million times and see what comes out faster.

:lolflag:

What's funnier is that I think I just might do that...

---

### Post by Jessehk on 2008-06-12
I don't know much about the internals of C++, but I do know a *little* bit. In this case, I can tell you that if a function is declared **virtual** in C++ (that is, declared so that it can be redefined in a derived class) , than every time it is called, there is a bit of overhead since the compiler has to do some sort of table lookup. 

Other than that, I would *guess* that the time would be equivalent.

---

### Post by Zugzwang on 2008-06-13
> **Sinkingships7 said:**
> 
Which way is faster:

a.) my_string_length = strlen(my_string);
OR
b.) my_string_length = string_object.string_length(my_string);


It depends: If the "string_length" function of string_object is static, than it's totally equivalent. If you meant "my_string.string_length()" instead of "string_object.string_length(my_string)", then it's equivalent, too (provided that string_length is non-virtual, as Jessehk wrote). If however you really meant "string_object.string_length(my_string)" and string_length is *not* a static member of string_object or its underlying class, then "string_object.string_length(my_string)" is slower since internally this is a call to string_object::string_length(string_object *this, whatever my_string), so two parameters are passed.

Also if my_string is not a pointer type please keep in mind that the string might be duplicated when calling (copy-constructor called).

---

### Post by Paul Miller on 2008-06-13
On modern hardware, the difference is negligible.

---

