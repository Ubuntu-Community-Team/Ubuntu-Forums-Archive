---
title: "structure for Super IO chip detection"
date: 2010-11-18
forum: Programming Talk
---

### Post by jamesbon on 2010-11-18
On this link
[http://lxr.free-electrons.com/source/drivers/parport/parport_pc.c?v=2.6.29#L97](http://lxr.free-electrons.com/source/drivers/parport/parport_pc.c?v=2.6.29#L97)
they defined a structure superio_struct and initialized as 
```
superios[NR_SUPERIOS] = { {0,},};
```
I am not able to understand above initialization has what is it getting initialized to.

What I deduce till now is superios is a structure array of struct superio_struct
and NR_SUPERIOS is defined as 3 hence an array of structure of size 3 
but 
```
superios[0]=??
superios[1]=??
superios[2]=??

```
This part is not clear to me as to what these individual members are initialized to.

---

### Post by Npl on 2010-11-18
per c standard, arrays and structures which get only partially initialized will have the remaining elements zero-initialised.
So everything is set to 0.

---

### Post by NathanB on 2010-11-18
It often helps to study other's code.  Take a look at psensor:

[http://freshmeat.net/projects/psensor](http://freshmeat.net/projects/psensor)

---

### Post by jamesbon on 2010-11-19
> **Npl said:**
> per c standard, arrays and structures which get only partially initialized will have the remaining elements zero-initialised.
So everything is set to 0.

Where is that documented and which C standard are you referring to?

---

### Post by spjackson on 2010-11-19
> **jamesbon said:**
> Where is that documented and which C standard are you referring to?
In the ISO C99 standard, this is covered in section 6.7.8, paragraph 21.

I don't have a copy of the ISO C89 standard, but it is covered in K&R (second edition) under Appendix A, A8.7 Initialization, as well as in the body of the text.

Any decent C primer must cover this.

---

### Post by jamesbon on 2010-11-20
In the K R appendix  what you said I read it twice.The examples in that appendix talk about 2 dimensional  array and say that initializer list can end with comma.
So 
```
initializer:assignment-expression {initializer-list,} 
```is a valid thing.According your books appendix.
What I do not get is what is **initializer**,**assignment-expression** and **initializer-list** in my example.
```
superios[NR_SUPERIOS] = { {0,},};
```Also I am not getting is why did some one need to initialize the structure to zero as said above.
If I leave the array without initializing then wont it remain zero if that is the whole and sole purpose of such initialization.
Why did the guy used 2 commas .It is only one dimensional array these commas were some thing which made it difficult to understand.


I googled for [http://www.google.com/search?hl=en&q=ISO+99+section+6.7.8%2C+paragraph+21.&aq=f&aqi=&aql=&oq=&gs_rfai=]("http://www.google.com/search?hl=en&q=ISO+99+section+6.7.8%2C+paragraph+21.&aq=f&aqi=&aql=&oq=&gs_rfai=") and there was no such thing you mention and if this link [http://gcc.gnu.org/c99status.html](http://gcc.gnu.org/c99status.html)
is what you mean then I don't think that I reached correct thing.

---

### Post by spjackson on 2010-11-20
> **jamesbon said:**
> In the K R appendix  what you said I read it twice.The examples in that appendix talk about 2 dimensional  array and say that initializer list can end with comma.
So 
```
initializer:assignment-expression {initializer-list,} 
```is a valid thing.According your books appendix.
What I do not get is what is **initializer**,**assignment-expression** and **initializer-list** in my example.
```
superios[NR_SUPERIOS] = { {0,},};
```Also I am not getting is why did some one need to initialize the structure to zero as said above.
If I leave the array without initializing then wont it remain zero if that is the whole and sole purpose of such initialization.
Why did the guy used 2 commas .It is only one dimensional array these commas were some thing which made it difficult to understand.


I googled for [http://www.google.com/search?hl=en&q=ISO+99+section+6.7.8%2C+paragraph+21.&aq=f&aqi=&aql=&oq=&gs_rfai=](http://www.google.com/search?hl=en&q=ISO+99+section+6.7.8%2C+paragraph+21.&aq=f&aqi=&aql=&oq=&gs_rfai=) and there was no such thing you mention and if this link [http://gcc.gnu.org/c99status.html](http://gcc.gnu.org/c99status.html)
is what you mean then I don't think that I reached correct thing.
Here are some relevant excerpts from K&R A8.7.

"An aggregate is a structure or an array. If an aggregate contains members of aggregate type, the initialization rules apply recursively." Here we have an array of structures: the outer braces initialize the array, and the inner braces initialize the structure which is the first element.

"The initializer for a structure... If there are fewer initializers in the list than members of the structure, the trailing members are initialized with 0."

"The initializer for an array... If the array has fixed size, the number of initializers may not exceed the number of members of the array; if there are fewer, the trailing members are initialized with 0."

From the grammar presented in this section, you can deduce that the trailing comma in the structure initializer is optional, as is the trailing comma in the array initializer. Some people, as a matter of style, prefer a trailing comma to indicate to the reader (not the compiler) that the remaining members are default initialized.

You are right that since the variable in question is static, not auto, it would be 0 initialized anyway, even if the programmer did not make this explicit. Specifying the initializer here is therefore optional and a matter of style.

The ISO C Standard is a document published by ISO; both paper and pdf versions are available (e.g. from ANSI or perhaps from your local ISO member organization). It is** the** definition of the C language. Like most copyrighted books, it is not searchable online as far as I know, so googling for it won't work.

---

### Post by jamesbon on 2010-11-22
Thanks I am clear with this now.I was not able to understand what you messaged just above even though I re read K  R several times.

---

