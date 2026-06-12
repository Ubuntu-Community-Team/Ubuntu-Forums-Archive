---
title: "High Level Function/Data Implementation"
date: 2009-04-07
forum: Programming Talk
---

### Post by Mr.Macdonald on 2009-04-07
I am working on a lisp style programming language and I was wondering how one would seamlessly implement "Data" and "Function".

A means of simplifing the problem, is to assume that data is just a function. Only upon evaluation, it returns "itself" but really just the data.

I am stuck in a philisophical wormhole!!

---

### Post by CptPicard on 2009-04-07
I really don't quite get what you mean, but I suggest you read *Structure and Implementation of Computer Programs*, in particular that part where they implement a Scheme in Scheme. I have this feeling you're talking about eval and apply and implementing code as data and vice versa...

---

### Post by Shin_Gouki2501 on 2009-04-07
[http://clojure.org/](http://clojure.org/)
:)

---

### Post by Mr.Macdonald on 2009-04-07
I am not even close to approaching the read/eval loop yet. I am talking about the low-level data holders. Like a struct to hold the numbers.

This is a generic number.
```
typedef struct {
  double real;
  double imag;
} number;
```
This number can handle all real and imaginary numbers (within precision).


I am looking for a generic data type, one that not only can hold numbers but also strings, symbols, and best of all functions.



I haven't even begun the parser for my lisp. I am trying to construct a framework for the lisp, such one that can have a parser attached to it and work flawlessly. Also the frame should be extendable by the average programmer. Simply because I don't know what everyone would want in a language.

---

### Post by soltanis on 2009-04-07
Do it the way I saw a Lisp interpreter written in C do it. You first of all know about how the linked lists work right

```

struct list {
 void *car;
 void *cdr;
}

```

Then of course you have

```

void *car(struct list *l)
{
 return l->car;
}

void *cdr(struct list *l)
{
 return l->cdr;
}

```

So now need some sort of symbol table (make it a list, because lists are good)

```

struct list *table;

struct symbol {
 int type;
 char *data;
}

/* allocate memory for table */
struct symbol s;
s.type = TYPE_WHATEVER;
s.data = &code_section;
table->car = &s;
table->cdr = NULL;
/* ... */

```

Okay, I'm starting to understand your dilemma.
If you take a peek at a source for a Scheme interpreter in C (they're surprisingly not that long) you'll see what I mean here. Scheme "compilation" is basically internalizing the lists represented in the Scheme code into this list and symbol table in memory. I forgot exactly how symbol representation goes (but I think for things like functions, what it did was jump to a particular node in the table and continue execution there).

Sorry for vagueness. I'm sure you've already thought of most of this.

---

### Post by kjohansen on 2009-04-07
> **Mr.Macdonald said:**
> 

I am looking for a generic data type, one that not only can hold numbers but also strings, symbols, and best of all functions.



Isnt this exactly the concept of an S-Expression?  When I implemented a lisp interpreter I had a basic s-expression class that held a string and had S-Exp children for car and cdr. Some booleans for flagging atomic, int etc also came in handy.

If you have an interpreter then it can parse any s-expression and thus you can have a function, int, etc in this s-expression.

---

### Post by CptPicard on 2009-04-08
Oh, now I get it...

IMO what you need is a data object type system first. Build a "struct object" that carries some sort of pointer to type information, and then a data pointer. You can do the struct-slicing magic to get some sort of polymporphism on the structs if you want to. Function objects are included in this model trivially of course.

Then, you can build one of the most important datatypes beside the primitives -- the "cons" which has the car and the cdr. The cons nests into the lists, of course.

The hardest part is to build the allocator/deallocator system for your data items... I guess you might want to use the gc library.

---

### Post by Mr.Macdonald on 2009-04-08
I do have a way of modelling pairs, linked lists, maps, evironments. I based everything off the "pair" just as lisp does. I do have a means of allocating automatically, and dynamically deallocating but based upon demand (you must call a function explicitly). And with test programs, I don't have memory leaks (valgrind!!).

My approach to data was to implement a structure holding a function
  void* (*evaluate)(void* args, environment* env);
and
  environment* args

I thought this would be a good way because a function could be represented in this way (obviously). Also, the arguments to the said function could be held in the environment. The environment is simply a map of data to cstrings (data being what I am representing). This seems to be a flawless way of repreasenting functions. But what about data, I chose to have a global function called the "constant function". This would take the arguments required of an evaluate function, only upon evaluation, it returns the value of the first argument. In a normal data object, this would be another data object, causeing a loop. But I would trick the system and instead have a int pntr or a cstring as the first argument. Thus avoiding the loop, this also allows constants to be replaced by functions.

The problem, is that their is no way to control the data put into the function, I wouldn't be able to check if the pntr passed in is a cstring or an int (for a constant) and thus not being able to free the pntr!!

---

### Post by Shin_Gouki2501 on 2009-04-09
i remember very fuzzy someone babbling about how a function pointer in C/C++ differs from a function in a functional language ( or even functional-object oriented language) 
i guess that's your problem.

---

### Post by CptPicard on 2009-04-09
Well, I once again got lost and don't quite understand the problem :)

I mean, what you want to have is the combination of eval/apply plus environments. Then, a function at its simplest just the list of code to be evaluated, plus environment bindings in force for lambda expression (the associated closure).

You said you're not at the eval/apply point yet, but I have a feeling that you should be...

---

