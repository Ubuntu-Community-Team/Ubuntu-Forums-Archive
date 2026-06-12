---
title: "constant static members within c struct"
date: 2008-03-11
forum: Programming Talk
---

### Post by rbprogrammer on 2008-03-11
ok, so this is my "proposed" struct:
```

struct formatter
{
    static char const * const replacestrings[][2] =
    {
        {" ","_"},
        {NULL, NULL}
    };
};

```
obviously the struct and char*[][] will have more to it, but the basic idea is this structure will hold information about files, that will then be formatted.  and [FONT="Courier New"]replacestrings[/FONT] will be a constant pointer to a 2-dimensional array that will be used for a text replacement operations.  and the last element ( ie {NULL, NULL} ) is used for iterating through from a loop without another variable for the size.  just to help eliminate errors if i were to add a new set of strings and forgot to increment the size variable.

what i want is to have everything that is going to be replaced declared within the variable ( so that it is all known at compile time ).  I do not need multiple copies of this for all the variables declared of type [FONT="Courier New"]formatter[/FONT], that is why i need it static.

i have tried multiple ways of declaring a static member like this, but nothing seems to compile.  also, it needs to be standard c since i am working on a project for my systems programming class and the language is c ( ie. not c++ )

i think i explained everything.  is this even possible to declare a constant static member within a standard c struct??

---

### Post by LaRoza on 2008-03-11
You can't define functions in structs in C.

You can put pointers to functions, if you wanted, but I don't see the point for this.

---

### Post by hod139 on 2008-03-11
Short answer, you can't.  In C, static limits the scope of the variable to the file or local function, there is no notion of a static "member" (there are no notions of classes).  For static member data, you need C++.

---

### Post by ray bot on 2008-03-11
I suppose you could make a function that acts as a constructor for formatter.  Basically it would malloc a new formatter, initialize formatter->replacestrings to the value you want, and return a pointer to the new formatter.

---

### Post by hod139 on 2008-03-11
> **ray bot said:**
> I suppose you could make a function that acts as a constructor for formatter.  Basically it would malloc a new formatter, initialize formatter->replacestrings to the value you want, and return a pointer to the new formatter.
How would that allow sharing of replacestrings among different formatter's?  Each instance would have it's own replacestrings.

I think the only thing you can do is have 
```

static char const * const replacestrings[][2] =
    {
        {" ","_"},
        {NULL, NULL}
    };

```in a separate file, include that file, and hope nothing else uses that name.  Maybe call it formatter_replacestrings or something.  No matter what, I don't think there is a good way in C to share data among structs (hence C++).

---

### Post by rbprogrammer on 2008-03-11
maybe i didnt explain the situation as good as i should of.  i dont need functions with in the struct, i just wont a variable that is only in scope from within the struct.  but i dont want a copy of the variable in every instance of the formatter structure, i just want the variable shared by all instances.  for example if i declare this:
```

struct formatter f;
struct formatter g;

```
then i want to be able to do:
```

f.replacestring[x][y];
//or
g.replacestring[y][x];

```
obviously those statements dont do anything, but i want the variable to be within the structure but only one copy.  no need for the same data to be copied over and over for all instances it the structure.

---

### Post by LaRoza on 2008-03-11
> **rbprogrammer said:**
> maybe i didnt explain the situation as good as i should of.  i dont need functions with in the struct, i just wont a variable that is only in scope from within the struct.  but i dont want a copy of the variable in every instance of the formatter structure, i just want the variable shared by all instances.  for example if i declare this:
```

struct formatter f;
struct formatter g;

```
then i want to be able to do:
```

f.replacestring[x][y];
//or
g.replacestring[y][x];

```
obviously those statements dont do anything, but i want the variable to be within the structure but only one copy.  no need for the same data to be copied over and over for all instances it the structure.

Do you know about pointers?

---

### Post by rbprogrammer on 2008-03-11
> **LaRoza said:**
> Do you know about pointers?
oh yea, i know pointers, that stuff is cake....

i guess what i am trying to get at is having one copy of constant data that is only in scope from within the structure.

from doing extensive googling, it looks like what i am trying to do is only *legal* in c++ with classes.

---

### Post by Wybiral on 2008-03-11
I think what LaRoza what saying is that you can create a global variable (or allocated on the heap) that each struct instance contains a pointer to. Why do you need this?

---

