---
title: "C programming"
date: 2009-10-11
forum: Programming Talk
---

### Post by vksingh on 2009-10-11
Hi,

I have made a static function  in a .c file and want to access it from other file.

I am getting the following build error:

Undefined reference to "function".

but if I remove the "static" keyword from the prototype of the function, It  works fine.

So, how to access a static function from another file.

Please help...........................  :(

---

### Post by matmatmat on 2009-10-11
I don't think you can, doesn't static mean only functions in that file can see it?

---

### Post by MadCow108 on 2009-10-11
static in front of a function in C means the function is only visible in the compilation unit the file is in. This mostly means you can't use it other source files.
Remove the static and it will work. The only drawback is very slightly less good optimizations of the compiler, better maintainability of separate compilation units outweighs this by far.

The alternative would be to put the static function inlined in a header file and include it in the other file.

it has nothing to do with static variables in C or even static member functions/members of C++.
These are completely different meanings of static.

---

### Post by nvteighen on 2009-10-11
Static functions are only useful when you need a function to be "private" to a certain module. If you want to use that function in more than a single module, then making it static will be useless... and the idea of inlining it into a header won't work because the linker will detect a name redefinition.

I guess your situation may be as follows: you want a function to be used just in some places. The best solution is to create a private header that provides the function's signature; include that header only in those places you want access to that function... Where you haven't included that header, you'll still be able to access the function via some pointer techniques, but not in a regular function call.

---

### Post by MadCow108 on 2009-10-11
inlining it in header will work because of the static, without you have a name redefinition
but that may blow up your executable size. A function that should be private should stay private.
I can't really think of a situation where header inlining would be an advantage, I just wanted to mention the possibility.

---

### Post by nvteighen on 2009-10-11
> **MadCow108 said:**
> inlining it in header will work because of the static, without you have a name redefinition
but that may blow up your executable size. A function that should be private should stay private.
I can't really think of a situation where header inlining would be an advantage, I just wanted to mention the possibility.

You're right. There's no redefinition because static avoids symbol exporting completely. But yes, it's totally impractical to inline such things there.

---

