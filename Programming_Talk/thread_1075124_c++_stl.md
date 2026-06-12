---
title: "c++ stl"
date: 2009-02-19
forum: Programming Talk
---

### Post by cybo on 2009-02-19
i have started learning c++ and just heard about stl. it seems like a very powerful tool. i have 2 questions:

1) does anyone know a really good tutorial on stl, specifically strings?
2) is there any other way to print strings without using std::cout and std::endl?

thanks

---

### Post by the_unforgiven on 2009-02-20
> **cybo said:**
> 
1) does anyone know a really good tutorial on stl, specifically strings?
[http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)
> **cybo said:**
> 
2) is there any other way to print strings without using std::cout and std::endl?

Depends on what you mean by 'other way'.
In C++, std::cout points to the stdout (in C parlance).
So, it's the only C++ way to print strings on screen.

---

### Post by jimi_hendrix on 2009-02-20
stl == standard template library in C++...

---

### Post by cybo on 2009-02-20
> **the_unforgiven said:**
> [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

Depends on what you mean by 'other way'.
In C++, std::cout points to the stdout (in C parlance).
So, it's the only C++ way to print strings on screen.

can i use printf or fprintf

---

### Post by johnl on 2009-02-20
> **cybo said:**
> can i use printf or fprintf

You can, but it is not a good idea to mix calls to std::cout with printf or fprintf;  you might see strange behavior.

---

### Post by monkeyking on 2009-02-20
> **johnl said:**
> You can, but it is not a good idea to mix calls to std::cout with printf or fprintf;  you might see strange behavior.

What kind of strange behavior?
I'm always using a mix of printf and std::cout.

They are both quite usefull.
You can't change the output precision at runtime with printf like

[PHP]
#DEFINE DEC 2
printf("%.DECf");
[/PHP]
with cout you have iomanip and setw setprecision.

But then again, If you have to type 
[PHP]std::cout << "var1:\t" << var1 << "var2\t" << var2 << std::endl[/PHP]
instead of
[PHP]printf("var1:%f\tvar2%f\n",var1,var2)[/PHP]
You would go crazy from all extra typing.

The real reason to use cout is that  you are basicly using a output stream,
and it's very easy to change to filewriting etc.

You would have to use fprintf in the c way

---

### Post by johnl on 2009-02-20
I agree, the verbosity of printing something in C++ really kills me:
```

std::cout << std::setprecision(3) << std::setwidth(4) << std::hex << foo

```
Well, you get the idea :)


The issue here is that both cout and printf() will buffer data (for performance reasons) before writing it to the console.  As a result, you can see output show up in a different order than you expect when mixing printf() and std::cout, unless you are flushing the streams between each usage.

---

