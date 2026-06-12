---
title: "C++ pointers - Which do you prefer?"
date: 2015-05-17
forum: Programming Talk
---

### Post by Gustaf_Alhll on 2015-05-17
I was curious on how people declare pointers, since we all do it differently.

There are usually four different ways (Just to give you a picture of what this is all about):
[LIST]
[*]Object* Variable 
[*]Object *Variable 
[*]Object * Variable 
[*]Object*Variable (Yes, this works) 
[/LIST]
 Which one do you prefer?
I personally prefer the last one, since that gives space it's own meaning (Eg. Pointers are dynamic values and spaces are static values).

And please, respect each others oppinion. I don't want people to fight about which one is better than the other. Apart from that, there is no "right" way to do it, it all a matter on what people prefer.

---

### Post by TheFu on 2015-05-17
> **Gustaf_Alhll said:**
> I was curious on how people declare pointers, since we all do it differently.

There are usually four different ways (Just to give you a picture of what this is all about):
[LIST]
[*]Object* Variable 
[*]Object *Variable 
[*]Object * Variable 
[*]Object*Variable (Yes, this works) 
[/LIST]
 Which one do you prefer?
I personally prefer the last one, since that gives space it's own meaning (Eg. Pointers are dynamic values and spaces are static values).

And please, respect each others oppinion. I don't want people to fight about which one is better than the other. Apart from that, there is no "right" way to do it, it all a matter on what people prefer.

Actually, there is "a right way" and that is whatever the development team standardizes on. Consistency within a project is critical to avoiding stupid mistakes.  Code formatters should enforce whatever that standard is for the project at check-in.

Personally, I like 
```
Object* Variable=NULL;
```  Always initialize everything to a known value. Do not trust different compilers to behave the same way. Some will zero all the memory, some will not.
For the declaration - being a pointer **is** part of the object type, after all.  I've never seen the last 2 options used anywhere.

---

### Post by spjackson on 2015-05-17
> **Gustaf_Alhll said:**
> I personally prefer the last one, since that gives space it's own meaning (Eg. Pointers are dynamic values and spaces are static values).

I agree that there is no right way; however I do find this strange. Assigning meaning to white space does not strike me as idiomatic C++. Do you use the same reasoning for references? Also, you cannot apply the same logic when you use smart pointers rather than naked pointers.

My order of preference is as follows (and the same applies to references as well as pointers).

[LIST=1]
[*]Object* Variable; You find this style in all the best C++ books (Stroustrup, Sutter, Meyers, Josuttis etc.) I regard this as "normal" C++ style.
[*]Object * Variable; I have used this in the past.
[*]Object *Variable; This is more commonly found in the C community in my experience.
[*]Object*Variable; I don't recall ever coming across this and I find it grating.
[/LIST]

---

### Post by ofnuts on 2015-05-18
Before C++ I used to go with 
```

Type *pointer;

```
because you can always do
```

Type x = *pointer;

```

But with C++ references this doesn't make sense, so references are better written:
```

Type& reference;

```
and to keep thing coherent
```

Type* pointer;

```

---

### Post by Rocket2DMn on 2015-05-18
I also vote for viewing the fact that a variable is a pointer as part of the type rather than the name. I prefer
```
Object* variable
```
I've seen plenty of options 1-3 though.
However, the language does not necessarily behave this way.  For example, if you declare multiple variables on one line (which I generally recommend against), you have to specify the * for each one:
```
Object *var1, *var2, *var3, ...
```
If you must declare multiple variables on a single line, please do everybody a favor and don't mix pointers and non-pointers!

---

### Post by TheFu on 2015-05-18
> **Rocket2DMn said:**
> 
```
Object *var1, *var2, *var3, ...
```


Everywhere I've worked, THIS was against our style guides and would be flagged as an **critical failure** in any code review. It is a good way to hide errors.

---

### Post by Rocket2DMn on 2015-05-18
> **TheFu said:**
> Everywhere I've worked, THIS was against our style guides and would be flagged as an **critical failure** in any code review. It is a good way to hide errors.

I completely agree.  Unfortunately, not all code is thoroughly reviewed and people still do this.  A programmer needs to be aware (and wary!) of this approach and understand why it so.

---

### Post by ofnuts on 2015-05-18
Things aren't that clear-cut IMHO. This is also a good way to show that all these variables must be the same type (and makes it easier to change the type if necessary).And if it were so bad why would the compiler allow it... after all in modern C/C++ the compiler will normally complain if you try to assign a type to its pointer.

---

### Post by TheFu on 2015-05-18
There are many things which are possible in this world that are a bad idea for unexpected or expected reasons. It is up to us to select which things are smart and which things should be avoided.  

It is not about making the compiler happy. That is a beginner, single-programmer, perspective.  It is about working well within a team and helping each other avoid making mistakes with new and existing code when in a hurry. There are many different techniques that I've learned over the years to have my code break at compile time instead of runtime. Compile time errors are easy to find.  Runtime errors, not so much.

Oh ... and "modern compilers" have been around 30+ yrs. ;)

---

### Post by trent.josephsen on 2015-05-18
I'm having a hard time thinking of an error that you could cause by leaving off a * in a declaration that wouldn't be caught at compile time. Perhaps it's because I'm not familiar with C++ in an area where it differs from C, or maybe I just lack imagination. Care to give an example?

---

### Post by lisati on 2015-05-18
> **spjackson said:**
> 
Object*Variable; I don't recall ever coming across this and I find it grating.


Agreed. There's a hint of ambiguity about it - are we dealing with pointers or multiplication? :D

---

### Post by Ankush_Menat on 2015-05-19
In C I prefer... I am not much into C++
type* var;

Read more here - [http://www.stroustrup.com/bs_faq2.html#whitespace](http://www.stroustrup.com/bs_faq2.html#whitespace)

---

