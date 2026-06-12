---
title: "How to access a function's definition in &quot;vim&quot;?"
date: 2010-06-23
forum: Programming Talk
---

### Post by jeremy28 on 2010-06-23
Hi all!
 
I'm using ubuntu 9.04;
Is there a complete library for C++ programming in ubuntu like "MSDN"?!
When using "Vim", I want to access a function's complete definition such as it's header file, library description and parameters, etc.
 
Is it necessary to install something from repository to obtain such a documentation?  
And what would be the command to access a function's description in "vim"?
 
TIA

---

### Post by trent.josephsen on 2010-06-23
> **jeremy28 said:**
> Hi all!
 
I'm using ubuntu 9.04;
Is there a complete library for C++ programming in ubuntu like "MSDN"?!
What do you mean by "complete"?  You can do many things with the C++ standard library without using platform-specific stuff.  For stuff like GUIs, there is no standard bearer, and you will need to pick a library yourself.

> When using "Vim", I want to access a function's complete definition such as it's header file, library description and parameters, etc.
 
Is it necessary to install something from repository to obtain such a documentation?  
And what would be the command to access a function's description in "vim"

Assuming there's a man page for it, position your cursor over the name of the function and hit Shift-K.  It's not a perfect solution, but TBH I'm not sure exactly what you're looking for.

---

### Post by MadCow108 on 2010-06-23
For the language C++ itself there are many references.
My favorite one is:
[http://www.cplusplus.com/reference/](http://www.cplusplus.com/reference/)

the linux system C api is mostly documented here:
[http://www.gnu.org/software/libc/manual/](http://www.gnu.org/software/libc/manual/)
and of course the manpages

there is no "including all" reference for ubuntu as there is for windows where most applications use the Microsofts tools.
In unix as you have many many frameworks/toolkits to build your application which each have their own documentation.

what comes closest to your second request is probably omnicompletion:
[http://vim.wikia.com/wiki/C%2B%2B_code_completion](http://vim.wikia.com/wiki/C%2B%2B_code_completion)
but as you see its needs work to set up, is slow and not too reliable in my experience.
If you need these features I suggest using an IDE like netbeans or Eclipse.

---

