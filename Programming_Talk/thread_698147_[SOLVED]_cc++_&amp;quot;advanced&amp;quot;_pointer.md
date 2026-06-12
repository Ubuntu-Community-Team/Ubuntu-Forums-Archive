---
title: "[SOLVED] c/c++ &amp;quot;advanced&amp;quot; pointers question"
date: 2008-02-15
forum: Programming Talk
---

### Post by rbprogrammer on 2008-02-15
ok, i have seen a few "advanced" ways of using pointers and i am trying to figure out what is really declared in these unique declarations.  since programming is kind of my thing, i am somewhat baffled at some of these.  this is what i have seen:
[LIST=1]
[*]double *a[n];
[*]double (*b)[n];
[*]double (*c[n])();
[*]double (*d())[n];
[/LIST]
my assumptions of these are reasonable at best, for some.  now i used two references to determine the exact order of operations of c++.  one if from a deitel&deitel book, and the other is  [http://www.cppreference.com/operator_precedence.html](http://www.cppreference.com/operator_precedence.html) . both agree, at least in the aspect of the two operators in question ( dereference and array access operators ).   and this is what i think is going on.

#1)  this is a pointer that holds the address of the first element of an array of n elements of type double.
#2).  b/c of the order of precedence, this is the same as #1.  ie a pointer that holds the base address of an array of n elements.
-----> now here is where my knowledge gets tested
#3).  ummm..... a pointer to an array of n elements ... yada, yada, yada ... address of ... yada, yada, yada ... function :confused:
#4).  this one is a pointer (called "d") that points to the address of a function that returns an array n elements long of type double.

am i at least close to right??  for 1,2,4 i think i have reasonable guesses, but #3 i just have no idea...... :confused:

---

### Post by stroyan on 2008-02-16
The c++decl command in the cdecl package can be very helpful sorting these out.
You do need to drop the 'n' or change it to an integer constant.
```
$ c++decl
Type `help' or `?' for help
c++decl> explain double *a[5];
declare a as array 5 of pointer to double
c++decl> explain double (*b)[5]
declare b as pointer to array 5 of double
c++decl> explain double (*c[5])()
declare c as array 5 of pointer to function returning double
c++decl> explain double (*d())[5]
declare d as function returning pointer to array 5 of double
c++decl> exit
$
```

---

### Post by Zwack on 2008-02-16
> **rbprogrammer said:**
> 
double *a[n];


A pointer to an n sized array of doubles.  It can also pretty much be written as double **a or
double a[x][n];

> 
double (*b)[n];


Ive never come across this in practice but I think that you might well be right.

> 
double (*c[n])();


a pointer to an array of functions that return double.  No, really. that's what I read that as.

> 
double (*d())[n];


An array of pointers to functions that return double.  Note that this is not quite the same as above, but in practice is indistinguishable...

I'm not entirely sure about this, and I'm sure I'll be corrected if I'm wrong but that is how I read these.

Z.

---

### Post by LaRoza on 2008-02-16
@OP A pointer to a function is written like so:

```

int (*putsTwo)(char*);

```
[php]
#include <stdio.h>
int main(int args,char ** argv)
{
    int (*putsTwo)(const char*);
    putsTwo = puts;
    putsTwo("Hello world");

}
[/php]

---

### Post by rbprogrammer on 2008-02-16
am i correct in thinking that because of the order of precedence, these two are equivalent??
```

double *a[n];
double (*b)[n];

```

---

### Post by aks44 on 2008-02-16
> **rbprogrammer said:**
> am i correct in thinking that because of the order of precedence, these two are equivalent??
```

double *a[n];
double (*b)[n];

```

No. See stroyan's post:

```
c++decl> explain double *a[5];
declare a as array 5 of pointer to double
c++decl> explain double (*b)[5]
declare b as pointer to array 5 of double
```

---

### Post by rbprogrammer on 2008-02-16
oh i see why... i feel stupid, i mixed up the order of precedence of the array access operator and the dereference operator.  i got it now.... thanks so much :guitar:

---

### Post by LaRoza on 2008-02-16
> **rbprogrammer said:**
> oh i see why... i feel stupid, i mixed up the order of precedence of the array access operator and the dereference operator.  i got it now.... thanks so much :guitar:

Don't feel stupid, everyone is confused by pointers at some point in their lives.

Extra credit:
```

char (*(*x[3])())[5];

```

---

### Post by Zwack on 2008-02-16
> **LaRoza said:**
> Don't feel stupid, everyone is confused by pointers at some point in their lives.

Extra credit:
```

char (*(*x[3])())[5];

```

Was that when the programmer sneezed while typing?   :D

Z.

---

### Post by LaRoza on 2008-02-16
> **Zwack said:**
> Was that when the programmer sneezed while typing?   :D

Z.

x is an array[3] of pointers to a function returning a pointer to an array[5] of char

---

### Post by rbprogrammer on 2008-02-17
> **LaRoza said:**
> 
...
Extra credit:
```

char (*(*x[3])())[5];

```

what the ....... now an extra credit for you Mr. LaRoza, where on earth would that come in handy?? :lolflag:

---

### Post by LaRoza on 2008-02-17
> **rbprogrammer said:**
> what the ....... now an extra credit for you Mr. LaRoza, where on earth would that come in handy??

(Just "LaRoza" please)

x is an array[3] of pointers to a function returning a pointer to an array[5] of char.

That may be useful in some situations, but it is not the type of programming I do.

---

### Post by rbprogrammer on 2008-02-17
> **LaRoza said:**
> 
(Just "LaRoza" please)

x is an array[3] of pointers to a function returning a pointer to an array[5] of char.

That may be useful in some situations, but it is not the type of programming I do.

lol, yea i dont think i will be using that notation in any programming that i will be doing :guitar:

---

### Post by LaRoza on 2008-02-17
> **rbprogrammer said:**
> lol, yea i dont think i will be using that notation in any programming that i will be doing

Don't you want to be a three start programmer?

[http://c2.com/cgi/wiki?ThreeStarProgrammer](http://c2.com/cgi/wiki?ThreeStarProgrammer)

---

