---
title: "Any easier way to do this?"
date: 2009-03-11
forum: Programming Talk
---

### Post by tneva82 on 2009-03-11
Little bit of problem. I have class X which is responsible for creating classes. It also gives out pointers to them when requested. For most of the purposes I have no problems but problem comes with certain type which can be used during the run of program.

BUT there's that one item that gives me problem. And the problem is there can be more than 1 references to **same** object and if you use it in one place it should be removed from every place(especially to avoid accessing pointer that was deleted elsewhere!).

Any easier way than to loop through every object which can contain pointers to it and remove that pointer from list? Guess that could be feasible but it feels like there should be better way.

Also just to verify. If I have list of pointers(list class) I can .erase() one of them and it won't affect the memory? Ie it still is there and if need be I can give pointer to it without issues? And if I have just reqular pointer like *pointer I can do pointer=0(and when using said pointer always check wether it's NULL or not) and no memory leaks happen(there's still pointer existing to said memory block(assuming I'm doing this right) which can be requested via the builder class mentioned)?

---

### Post by crazyfuturamanoob on 2009-03-11
[Quote=tneva82]Any easier way than to loop through every object which can contain pointers to it and remove that pointer from list?[/Quote]

What's wrong with that? I can't think of any other way.

---

### Post by tneva82 on 2009-03-11
> **crazyfuturamanoob said:**
> What's wrong with that? I can't think of any other way.

Mainly performance. Trying to figure out wether there would be way to optimise this one a bit(since my biggest worry ATM isn't can I get this working atleast somehow but can I get it working in speed it's actually usable :D). So ATM at the moment while designing next stage I'm trying to come up with ideas where current solution could be tuned up for faster(even if it takes up more memory. For example one solution I have come up will eat up quite a bit of RAM but should result in LOT less polygons drawn=saved rendering time. Still not going to be perfect but maybe it's enough for my not-so-complex models).

So guess the thread title is bit wrong. Should be faster way to do this.

---

### Post by dwhitney67 on 2009-03-11
> **tneva82 said:**
> Little bit of problem. I have class X which is responsible for creating classes. It also gives out pointers to them when requested. For most of the purposes I have no problems but problem comes with certain type which can be used during the run of program.

BUT there's that one item that gives me problem. And the problem is there can be more than 1 references to **same** object and if you use it in one place it should be removed from every place(especially to avoid accessing pointer that was deleted elsewhere!)...
I have no idea what you are stating above.  Can you elaborate a little more?

Maybe what you need to use is a shared_ptr?

Example:
```

#include <tr1/memory>
#include <iostream>

struct Foo
{
  int value1;
  int value2;
};

int main()
{
  std::tr1::shared_ptr<Foo> ptr1(new Foo);
  ptr1->value1 = 5;
  ptr1->value2 = 50;

  std::cout << ptr1->value1 << std::endl;

  std::tr1::shared_ptr<Foo> ptr2 = ptr1;

  // no need to delete anything!
}

```

---

### Post by crazyfuturamanoob on 2009-03-11
There might be a faster way to do it but with today's computers that iteration thing isn't a performance issue.

---

### Post by stroyan on 2009-03-11
> **tneva82 said:**
> 
Any easier way than to loop through every object which can contain pointers to it and remove that pointer from list? Guess that could be feasible but it feels like there should be better way.

Also just to verify. If I have list of pointers(list class) I can .erase() one of them and it won't affect the memory? Ie it still is there and if need be I can give pointer to it without issues? And if I have just reqular pointer like *pointer I can do pointer=0(and when using said pointer always check wether it's NULL or not) and no memory leaks happen(there's still pointer existing to said memory block(assuming I'm doing this right) which can be requested via the builder class mentioned)?

The list implementation does not promise that an element is still kept around when it has been passed to .erase().  list::erase() only promises that other elements and iterators on that list remain correct.

dwhitney67's shared pointer idea looks like a good start.  If you combine that with a boolean in each class that marks "done already" then you can use code that quickly skips (and erases) elements that are marked as done.  You won't have to deal with multiple references when you first erase one.  You will just have to take a little extra care during use of the references.

---

### Post by tneva82 on 2009-03-11
> **dwhitney67 said:**
> I have no idea what you are stating above.  Can you elaborate a little more?

Object X points to Object Y.
Object Z points to Object Y.

Object Y is removed. How to remove Object X and Object Z's references(which could be inside quite a nest of objects within objects) most efficiently(or more specifically from the list classes that contain the pointers). Any more efficient method than going through ALL objects and checking wether they have pointer to Object Y before deleting Object Y.

ATM if I remove reference from Object X and delete object Y there's still object Z which causes image to be drawn and if user clicks it it tries to use it. And since Object Y was deleted...Uh oh! I forsee segmentation fault.

One way it would be easy to check would be if it's possible to check wether pointer still points to valid memory or not. Ie if there's been no delete call then go through, if there's been delete this has been used so remove the element from list and continue. Not sure is that possible but that would probably be the most efficient way for this.

---

### Post by dwhitney67 on 2009-03-11
> **tneva82 said:**
> Object X points to Object Y.
Object Z points to Object Y.

Object Y is removed. How to remove Object X and Object Z's references(which could be inside quite a nest of objects within objects) most efficiently(or more specifically from the list classes that contain the pointers). Any more efficient method than going through ALL objects and checking wether they have pointer to Object Y before deleting Object Y.

So basically, you have one class that wants to provide a reference to an internal object to another class, and then renig on this "good will" by destroying the internal object.  Good luck with that; it seems like a big whole in your design.

> **tneva82 said:**
> 
ATM if I remove reference from Object X and delete object Y there's still object Z which causes image to be drawn and if user clicks it it tries to use it. And since Object Y was deleted...Uh oh! I forsee segmentation fault.

Keen observation, and quite correct.

> **tneva82 said:**
> 
One way it would be easy to check would be if it's possible to check wether pointer still points to valid memory or not. Ie if there's been no delete call then go through, if there's been delete this has been used so remove the element from list and continue. Not sure is that possible but that would probably be the most efficient way for this.

Re-examine your design; there's probably another approach that does not involve a kludge or substantial checking of pointers.

---

### Post by ByteJuggler on 2009-03-11
You might consider the Subject-Observer design pattern (also known as Publish/subscribe).  Any object that might be used by/observed by multiple other objects are "subject" objects, which are used or observed by "observer" objects.  If every user/observer of an object is registered as observer with the subject, then the subject can notify them when needed (e.g. when being destroyed.)  

Practically, it boils down to holding a list of observing objects which get notified about something (e.g. imminent destruction), allowing appropriate behaviour (e.g. setting to nil of a held reference for example.) You're basically trading space for speed, which in your case sounds like an acceptable tradeoff.

---

### Post by tneva82 on 2009-03-12
> **dwhitney67 said:**
> So basically, you have one class that wants to provide a reference to an internal object to another class, and then renig on this "good will" by destroying the internal object.  Good luck with that; it seems like a big whole in your design.

Well. The program needs to have access from multiple place to same object. And alas in this case that object will be removed(wether simply hidden from user and deleted from memory when program is closed or deleted outright there to ensure memory doesn't run out due to more and more objects waiting for deletion in hidden) sooner or later.

The objects in question will be deleted sooner or later(to ensure that I'll be doing that one in one centralised location. He who allocates new memory shall free it as well) but problem is references to that one.

> **ByteJuggler said:**
> You might consider the Subject-Observer design pattern (also known as Publish/subscribe).  Any object that might be used by/observed by multiple other objects are "subject" objects, which are used or observed by "observer" objects.  If every user/observer of an object is registered as observer with the subject, then the subject can notify them when needed (e.g. when being destroyed.)  


You know that's not half-bad idea. Need to find that book about those again and refresh myself on those and see how to incorporate that one to my design. That could very well work. And yeah bit of extra memory isn't issue so much as speed.

---

### Post by eye208 on 2009-03-12
> **tneva82 said:**
> Well. The program needs to have access from multiple place to same object. And alas in this case that object will be removed(wether simply hidden from user and deleted from memory when program is closed or deleted outright there to ensure memory doesn't run out due to more and more objects waiting for deletion in hidden) sooner or later.

The objects in question will be deleted sooner or later(to ensure that I'll be doing that one in one centralised location. He who allocates new memory shall free it as well) but problem is references to that one.
Do you remember when we advised you not to mix C and C++ but use containers instead of raw pointers? It seems you ignored that advice, and now you are screwed because there are [dangling pointers](http://en.wikipedia.org/wiki/Dangling_pointer) all over your program.

If you used containers, there wouldn't be a problem. For example, the [weak_ptr class](http://www.boost.org/doc/libs/1_38_0/libs/smart_ptr/weak_ptr.htm) from the Boost library does exactly what you need.

---

