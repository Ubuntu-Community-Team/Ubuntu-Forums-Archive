---
title: "How to install a CPAN module ?"
date: 2010-03-05
forum: Programming Talk
---

### Post by WitchCraft on 2010-03-05
Question:
I'm kinda Perl muffle, but now I need to convert IDL to C and C++...

I've managed to find these two here:
[http://search.cpan.org/~perrad/CORBA-C-2.62/bin/idl2c](http://search.cpan.org/~perrad/CORBA-C-2.62/bin/idl2c)
[http://search.cpan.org/~perrad/CORBA-Cplusplus-0.41/bin/idl2cpp](http://search.cpan.org/~perrad/CORBA-Cplusplus-0.41/bin/idl2cpp)

I think I once knew how to install a Perl module...
I think there was an easy tool, where you just had to enter the module name, and it installed.

I guess the answer should be simple for just about any Perl programmer...

---

### Post by Some Penguin on 2010-03-05
cpan -i CORBA::C
cpan -i CORBA::Cplusplus

might do it (as root).

---

### Post by WitchCraft on 2010-03-05
> **Some Penguin said:**
> cpan -i CORBA::C
cpan -i CORBA::Cplusplus

might do it (as root).

Thanks !
No problem, I am r00t. 
Is there any such thing for Windows, too ?

---

### Post by nvteighen on 2010-03-05
Hijacking... :P

What about installing it as normal user? It may sound a bit silly, but is there a way to install modules in user-wide space?

---

### Post by WitchCraft on 2010-03-05
> **nvteighen said:**
> Hijacking... :P

What about installing it as normal user? It may sound a bit silly, but is there a way to install modules in user-wide space?

Doesn't matter, it doesn't work with my IDL filez.
I wanted to have a .NET dll's IDL file transformed into a .cpp or a .c or a .h file.
But midl (MS IDL compiler) doesn't generate these because it crashes, missing either paths or .dlls.
(adding paths and dll's to ENV make it abort with error)
It worked with VB6, but maybe this is a Vista bug.

I was however able to grab that file from the Microsoft compiler's temp directory (once i found it)
%userprofile%/AppData/Local/Temp

;-))



> **nvteighen said:**
> Hijacking... :P

What about installing it as normal user? It may sound a bit silly, but is there a way to install modules in user-wide space?

Why don't you just su root ? Don't trust CPAN, isn't it? 
Well, neither do I, that's why I execute all those silly things like KeyGens and CPAN modules in a VM. You should try it, saves a lot of headache.

---

### Post by nvteighen on 2010-03-06
> **WitchCraft said:**
> 
Why don't you just su root ? Don't trust CPAN, isn't it? 
Well, neither do I, that's why I execute all those silly things like KeyGens and CPAN modules in a VM. You should try it, saves a lot of headache.

It's just that what if I just want to... :P

---

### Post by WitchCraft on 2010-03-06
> **nvteighen said:**
> It's just that what if I just want to... :P

Well, if you find out, let me know the answer. 
My question is answered, and since I don't know the answer to yours, I'll leave it unsolved for now, for you ;-))

I think based on the midl generated file, and the IDL file, and the C version of VB6, I'll be able to write a C++/C converter myself. C++ should be easy, C probably is not.
For including a C# .so in a C++ executable on Linux, I'm now trying out the mono embed way ;-))
Looks promising, the example works...
Hell, the mono website says you can embed mono on Windows, too, so I wouldn't need COM...
Just have to figure out how to use C mono with my C++ exe. I think extern "C" is just the thing I need ;-))

---

