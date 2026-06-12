---
title: "[C++]Virtual destructor"
date: 2011-12-02
forum: Programming Talk
---

### Post by ehmicky on 2011-12-02
Hi,

If I'm designing a library, should I always make destructors virtual, in case my users derive the class ?
Thanks :)

---

### Post by dagoth_pie on 2011-12-02
That's actually a little trap I fell into once. When you destroy a derrived class, it first calls it's own destructer, then it's super-class's constructor, and so on, all the way up the stack to the base class. You get lots of interesting errors if you try to make the destructor of an abstract class virtual.

---

### Post by SevenMachines on 2011-12-02
I would, but the c++ faq will give you what you need to make the decision
[http://www.parashift.com/c++-faq-lite/virtual-functions.html#faq-20.7](http://www.parashift.com/c++-faq-lite/virtual-functions.html#faq-20.7)
> **[20.7] When should my destructor be virtual?**


 When someone will delete a derived-class object via a base-class pointer. 
In particular, here's when you need to make your destructor virtual: 

[LIST]
[*]*if* someone will derive from your class,
[*]*and if* someone will say new Derived, where Derived is derived from your class,
[*]*and if* someone will say delete p, where the actual object's type is Derived but the pointer p's type is your class.
[/LIST]
 Confused?  Here's a simplified rule of thumb that usually protects you and usually doesn't cost you anything: make your destructor virtual if your class has *any* virtual functions.  Rationale: 

[LIST]
[*]that *usually* protects you because most base classes have at least one virtual function.
[*]that *usually* doesn't cost you anything because there is no added per-object space-cost for the second or subsequent virtual in your class.  In other words, you've already paid all the per-object space-cost that you'll ever pay once you add the first virtual function, so the virtual destructor doesn't add any additional per-object space cost.  (Everything in this bullet is *theoretically* compiler-specific, but in practice it will be valid on almost all compilers.)
[/LIST]
 Note: in a derived class, if your base class has a virtual destructor, your own destructor is automatically virtual.  You might need an explicitly defined destructor for other reasons, but there's no need to redeclare a destructor simply to make sure it is virtual.  No matter whether you declare it with the virtual keyword, declare it without the virtual keyword, or don't declare it at all, it's still virtual. 
BTW, if you're interested, here are the mechanical details of *why* you need a virtual destructor when someone says delete using a Base pointer that's pointing at a Derived object.  When you say delete p, and the class of p has a virtual destructor, the destructor that gets invoked is the one associated with the type of the object *p, not necessarily the one associated with the type of the pointer.  This is A Good Thing.  In fact, violating that rule makes your program undefined.  The technical term for that is, "Yuck." 


---

### Post by 11jmb on 2011-12-02
> **dagoth_pie said:**
> That's actually a little trap I fell into once. When you destroy a derrived class, it first calls it's own destructer, then it's super-class's constructor, and so on, all the way up the stack to the base class. You get lots of interesting errors if you try to make the destructor of an abstract class virtual.

That's not necessarily a trap, but something that you just need to understand how it works. What are these interesting errors you speak of? The only errors I have seen pertaining to virtual destructors are PEBCAK-type errors.


You need to try to predict whether users will inherit from this class. If you think they will, then you should usually make your destructor virtual, because otherwise you would not allow them to dynamically allocate any memory inside the child class, because they would have no facility to free it.

---

### Post by ehmicky on 2011-12-03
Thanks !

---

### Post by dazman19 on 2011-12-09
Also if you are making classes that hold lots of tiny bits of data. e.g. bit level stuff, then there is a memory overhead from using virtual destructors. I think they need at minimum 32bits, or the size of a pointer as the overhead. So you can imagine if you had LOTS of very tiny object lets say something represented by booleans or something small like single characters then you would not want to use them. However in most cases you would always want to use them to avoid leaks and so the abstract classes can manage memory for you when you call the destructors. I dont do a lot of C++, java is extremely forgiving when it comes to destructing objects and freeing memory. But if you are working at a slightly lower level with C++ then you may want to consider that, it really depends what you are doing.

---

### Post by 11jmb on 2011-12-09
Any virtual function will have a small memory overhead from its virtual table entry. that is not a unique property of a virtual destructor

I don't understand what addressing small primitives has to do with whether or not to include a virtual destructor. I agree  that having a 32 or 64-bit pointer to a 1 or 8-bit primitive is silly, unless there are many more of them at subsequent addresses (so an array).

I agree that you should usually be defining your single primitives on the stack, but I stick with my original assessment that any class that you expect to be inherited should have a virtual dtor.

---

### Post by karlson on 2011-12-09
> **dazman19 said:**
> Also if you are making classes that hold lots of tiny bits of data. e.g. bit level stuff, then there is a memory overhead from using virtual destructors. I think they need at minimum 32bits, or the size of a pointer as the overhead. So you can imagine if you had LOTS of very tiny object lets say something represented by booleans or something small like single characters then you would not want to use them. However in most cases you would always want to use them to avoid leaks and so the abstract classes can manage memory for you when you call the destructors. I dont do a lot of C++, java is extremely forgiving when it comes to destructing objects and freeing memory. But if you are working at a slightly lower level with C++ then you may want to consider that, it really depends what you are doing.

If you have lots of objects of tiny size like Java's Boolean with lots of virtual functions in them I suggest you rethink your design.

---

### Post by 11jmb on 2011-12-09
Also, I think its safe to say that if you are worried about 32 bits of memory overhead, you should probably not be using OOP to begin with.

---

### Post by karlson on 2011-12-09
> **11jmb said:**
> Also, I think its safe to say that if you are worried about 32 bits of memory overhead, you should probably not be using OOP to begin with.

Can't say I agree with that statement considering that Java's Boolean class would be exactly what was described: 2 bytes (value and is null) and at a minimum 32 for virtual table.  If you use a lot of Booleans it adds up.

---

### Post by 11jmb on 2011-12-09
Ah, I see what you are saying. Yes, when a class wraps a very small amount of data, the 32-bit pointer to the virtual table becomes more cumbersome, percentage-wise. Because of the slightly increased memory footprint your choice to make functions virtual should be deliberate, regardless of object size. 

I still think that it is better to steer clear of OOP as a whole if you are optimizing memory usage though (if you can). Good object oriented design will always produce larger binaries.

---

### Post by karlson on 2011-12-09
> **11jmb said:**
> Ah, I see what you are saying. Yes, when a class wraps a very small amount of data, the 32-bit pointer to the virtual table becomes more cumbersome, percentage-wise. Because of the slightly increased memory footprint your choice to make functions virtual should be deliberate, regardless of object size. 

I still think that it is better to steer clear of OOP as a whole if you are optimizing memory usage though (if you can). Good object oriented design will always produce larger binaries.

We are talking completely different things here.  Larger binaries may be acceptable, while larger memory footprint at runtime is not.  And optimizing memory usage doesn't mean you can't use OOP granted though that well written and well optimized assembly code might do a slightly better job of memory optimization but then again these are 2 very large caveats.

---

### Post by 11jmb on 2011-12-09
> **karlson said:**
> We are talking completely different things here.  Larger binaries may be acceptable, while larger memory footprint at runtime is not.  And optimizing memory usage doesn't mean you can't use OOP granted though that well written and well optimized assembly code might do a slightly better job of memory optimization but then again these are 2 very large caveats.

My comments about memory optimization were in response to this:
> 
if you are making classes that hold lots of tiny bits of data


not this:
> 
If you have lots of objects of tiny size like Java's Boolean with lots of virtual functions in them I suggest you rethink your design.


If you have a class with lots of small primitives, a 32 bit reference to the virtual table is not going to make a big difference. If you have lots of small objects, an extra 32 bits apiece is huge.

That said, a programmer's choice to make a function virtual (or choice to do anything, really) should be tasteful and deliberate.


As far as my comment about avoiding OO if you can, you might be surprised by how much extra memory it costs. Just as a very simple example, look at binary size for the C and C++ versions of HelloWorld (iostream/cout vs stdio.h/printf), compiled using the same exact commands. IIRC, the C++ version makes a binary that is about 10% larger, which is pretty significant when you are talking about memory optimization. I last did this in the dark ages :), so it may be slightly different these days.

EDIT: just tried it with g++ -Os, 8.9 KB vs. 8.2 KB, only 8.5% increase, but my point still stands

---

### Post by karlson on 2011-12-12
> **11jmb said:**
> 
As far as my comment about avoiding OO if you can, you might be surprised by how much extra memory it costs. Just as a very simple example, look at binary size for the C and C++ versions of HelloWorld (iostream/cout vs stdio.h/printf), compiled using the same exact commands. IIRC, the C++ version makes a binary that is about 10% larger, which is pretty significant when you are talking about memory optimization. I last did this in the dark ages :), so it may be slightly different these days.

EDIT: just tried it with g++ -Os, 8.9 KB vs. 8.2 KB, only 8.5% increase, but my point still stands

The size of the program after compilation becomes irrelevant unless you are working with an embedded device.  Especially so in modern systems.  Runtime is a completely different story.

---

