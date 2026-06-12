---
title: "C++ noob question."
date: 2013-03-11
forum: Programming Talk
---

### Post by 3v3rgr33n on 2013-03-11
Hi

I'm havin' difficulty understanding the difference between the two.
```

void someFunction(someType obj1);

```
and
```

void sameFunction(someType &obj1)

```

I understand that with the first example, when you call ```
someFunction
```, the parameter is going to be copied to ```
obj
```. One then needs to use other means which are not
as expensive.

Why would one pass the address as opposed to
passing a pointer --- specificaly, why do copy constructors not take a pointer but a reference instead?

Is it a matter of preference?

---

### Post by iMac71 on 2013-03-11
Perhaps the following two links may help you to understand the difference:
[http://www.cplusplus.com/doc/tutorial/functions/](http://www.cplusplus.com/doc/tutorial/functions/)
[http://www.cplusplus.com/doc/tutorial/functions2/](http://www.cplusplus.com/doc/tutorial/functions2/)

---

### Post by 3v3rgr33n on 2013-03-11
Hey

Thanx for the resources. Let me try to rephrase my question. Why would a person use
```
void someFunction(someType &var)
``` as opposed to
```
void someFunction(someType *var)
```. Is it a preference thing?

To my understanding, you cannot manipulate &var directly, you would need to create a pointer (within the scope of someFunction), pointing to that memory address, so why not just pass the pointer in the first place?

---

### Post by iMac71 on 2013-03-11
this additional link may help you to understand the difference of using & instead of *:
[http://www.cplusplus.com/doc/tutorial/pointers/](http://www.cplusplus.com/doc/tutorial/pointers/)

---

### Post by SledgeHammer_999 on 2013-03-11
> **3v3rgr33n said:**
> Hey

Thanx for the resources. Let me try to rephrase my question. Why would a person use
```
void someFunction(someType &var)
``` as opposed to
```
void someFunction(someType *var)
```. Is it a preference thing?

To my understanding, you cannot manipulate &var directly, you would need to create a pointer (within the scope of someFunction), pointing to that memory address, so why not just pass the pointer in the first place?

For the first example the variable is passed by reference. So any changes to the var will be automatically reflected to the original object. In the second example you will need to dereference the pointer in order to manipulate the data it points to.

Have a look at this [page](http://www.cplusplus.com/doc/tutorial/functions2/) for an explanation for arguments passed by reference vs arguments passed by value.

---

### Post by usernamer on 2013-03-11
tbh I'm a bit of a noob as well, and learning C as opposed to C++, so I could be wrong (but it sounds like the languages overlap here)...

I'm fairly sure (that at least in C), *var refers to the value at the address which the pointer, var points to, whereas &var refers to the memory address of var. At one (*), you're passing the value at the memory address of the thing being pointed to, and with the other (&), you're passing the memory address of the pointer (which points to the memory address of whatever it is var points to) into the function.

Hope that helps

---

### Post by r-senior on 2013-03-11
@usernamer: C++ and C do have the same syntax for working with pointers, but this is an additional feature of C++. It's a prefix to a function parameter or variable that says it is a reference. It uses the same "&" character as the "address of" in C, but it's not the same thing.

@OP: In the case of passing what you might call an "out" parameter, obviously the syntax of the pointer and reference is slightly different:

*Pointer*
```
void increment(int *x)
{
        *x = *x + 1;
}

int main()
{
        int value = 0;
        increment(&value);
        cout << value << endl;
}

```

*Reference*
```
void increment(int &x)
{
        x = x + 1;
}

int main()
{
        int value = 0;
        increment(value);
        cout << value << endl;
}

```

The result is the same in both cases.

But there's more to it than syntax. A reference is like a pointer with conditions attached:

[LIST]
[*]It can't be NULL
[*]It can't be reassigned to refer to something else
[*]It can't be manipulated, e.g. incremented to point at the next entry in an array
[/LIST]
Sometimes it's more appropriate to work with a pointer, e.g. if you want to work with the idea of null, or if you want to manipulate it. Other times it's a better fit to work with a reference. In the increment function above, I think a reference fits the intent of the function better than a pointer. (I don't want to manipulate it and it shouldn't be null).

---

### Post by SledgeHammer_999 on 2013-03-11
> **usernamer said:**
> 
I'm fairly sure (that at least in C), *var refers to the value at the address which the pointer, var points to, whereas &var refers to the memory address of var. At one (*), you're passing the value at the memory address of the thing being pointed to, and with the other (&), you're passing the memory address of the pointer (which points to the memory address of whatever it is var points to) into the function.

No you have it wrong. You should read more about **pointers**, but more specifically about declaring functions that take arguments and how you declare(and read) the type of each argument. If you omit the variable name this is more obvious. So for example

```
void myfunction(int);
```
Takes one argument of type int.

```
void myfunction(int*);
```
Takes one argument which is pointer to int
```
void myfunction(int&);
```
Take one argument of type int but instead of copying the value it references it (think pointer magic is happening behind the scenes)

And to show the different usages of &
```
int x = 10;
int *y = NULL; //pointer to int
y = &x; //y now points to same value of x

void myfunction(int &z)
{
   z = 15;
}

myfunction(x); //notice that you passed an int to the function and not an pointer to int.
//after this function call x will have a value of 15 and not 10

```

Also & can be used as a bitwise operator but this will confuse the hell out of you, so I don't provide an example.

Keep in mind that in C++ (and probably in C) the same keyword can have a different meaning depending on the context.

EDIT: **r-senior** beat me to it.

---

### Post by trent.josephsen on 2013-03-11
tl;dr - Don't learn C and C++ at the same time. :-P

---

### Post by r-senior on 2013-03-11
Just don't learn C++ ... #-o

<Turns laptop off and scurries off to bed>

---

### Post by spjackson on 2013-03-12
See [Bjarne Stroustrup's C++ Style and Technique FAQ]("http://www.stroustrup.com/bs_faq2.html"), in particular the answers to the questions:
[LIST]
[*]Why does C++ have both pointers and references?
[*]Should I use call-by-value or call-by-reference?
[*]I do want to change the argument, should I use a pointer or should I use a reference?
[/LIST]

---

### Post by 3v3rgr33n on 2013-03-12
Ok, I think I get it. Thanx guys

---

