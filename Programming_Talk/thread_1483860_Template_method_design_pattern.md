---
title: "Template method design pattern"
date: 2010-05-15
forum: Programming Talk
---

### Post by druca on 2010-05-15
Hi! 
I apologize for the awful book I'm about to write.

I was wondering if someone could help me with the Template design pattern for implementing different types of data structures underneath a general stack.

For example we are to make a list based stack implementation,
and an array one, that's the easy part.

But what I don't get is How the Template Design Pattern is suitable for making a general data structure, there is no "Template Method" for stacks etc, you can pop(), top() etc but those are by user demand and not in any algorithmic form like a sort. 

I tried making the constructor of the base the supposed "Template Method" and virtual calls like pop() etc, would go to the derived classes where the more specific data structure is but......is the base class stack just and empty shell? 

Is my professor on drugs or is abstract a completely different word for what I want to to?

Abstract as in the base class is abstract and empty and the derived classes implement the abstract...and then for some stupid reason you call the derived classes with a pointer to the base? This is supposed to be hidden from the user I assume, so that may be a stupid method. Maybe.  

I can actually make this into a character constant pointer,Then recast it into a function call, thereby calling a pseudo constructor of the derived class that I made.                                                                                                                                                         

Or is this supposed to be "Abstract" and empty, only to be implemented in the derived class? 

Sorry if I offended anyone,

Thank you and have a nice day

---

### Post by Some Penguin on 2010-05-15
Something like a stack can pop/push without caring what it's actually popping or pushing.  The code will basically be identical save for the size of the data being shoved around.

In C++, a template stack (such as found in STL) is slightly nicer than a stack designed to hold, say, void* to generic heap objects or the like, because you'll get type safety.

In Java, a template stack (generic, as they call 'em) is nicer than a pre-Java-5 stack that just takes Objects, for the same reason.

---

