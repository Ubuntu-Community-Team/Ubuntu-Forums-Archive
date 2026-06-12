---
title: "(another) C++ language question"
date: 2008-07-16
forum: Programming Talk
---

### Post by ceclauson on 2008-07-16
Hello!

I'm a programmer with a largely Java background who is now trying to program C++, and I have a question about how C++ handles object references and deleting.

In a program I'm writing, I have an algorithm that will create a large number of objects of various types (from different classes), and no common subclass.  I would like to cache pointers to these objects in a container (probably a list) so that they can all be deleted after I'm done with them.  If this were Java (besides the fact that I wouldn't be doing manual memory management...) I would create a collection (probably a linked list) of Object types, so I could store references of any kind in it.

However, C++ doesn't have any common superclass of all classes, so I'm not sure what type I should declare the list to be of.  I know that pointer-to-void (with void* syntax) is sometimes used for a generic pointer, should I use this?  If so, if I use the delete keyword to delete all of the the objects which are referenced by a pointer-to-void, will C++ be able to determine the object's type dynamically and delete it properly?

Thanks,
Cooper

---

### Post by Zugzwang on 2008-07-16
> **ceclauson said:**
> 
If so, if I use the delete keyword to delete all of the the objects which are referenced by a pointer-to-void, will C++ be able to determine the object's type dynamically and delete it properly?


No, it won't. C++ doesn't support such actions because normally there is no need to. Storing objects of a non-common base type is a no-no in C++ (and is usually a sign for bad design). So you would create lists for each individual type. 

However, if you still want to stick to your approach and you have different classes you can use Multiple Inheritance. So you modify each of your classes to derive from some class (let's say it's name is "Deleatable") and make a list of deletables. This deletable class has an abstract vistual destructor and then it works.

For checking if everything went correctly, you may want to use Valgrind to check your program at run time for memory leaks.

---

### Post by jim_24601 on 2008-07-16
No, void pointers wouldn't work. The memory would be deallocated but the actual object would not be destroyed.

Is there any reason that you need to put all your various objects in the one container? As you say, C++ does not have a great ueber-object from which all objects are derived, and I've never seen it as a shortcoming.

If you really need all the objects in one place, your options are to make your own ueber-object and derive everything from it, or wrap everything in some reference class. Neither is very satisfactory.

What algorithm are you going to apply to a group of unrelated objects in a bag, anyway?

---

### Post by dribeas on 2008-07-16
> **ceclauson said:**
> 
In a program I'm writing, I have an algorithm that will create a large number of objects of various types (from different classes), and no common subclass.  I would like to cache pointers to these objects in a container (probably a list) so that they can all be deleted after I'm done with them. [...]

However, C++ doesn't have any common superclass of all classes, so I'm not sure what type I should declare the list to be of.

I don't think that using a container to hold completely different things is a good design choice, even if you could. Anyway, learning a language is not just learning the syntax, else you would be programming Java in a C++ syntax, or C in a C++ syntax, both of which are possible but not quite desirable.

In a lot of cases you can use stack allocated objects, which will remove some of the penalties from dynamically allocated memory (requesting and releasing memory). But if you must use dynamically allocated memory (new) then you should avoid using plain raw pointers, but hold them in some manager facility that takes care of releasing the resources using RAII. Consider using std::auto_ptr<T>:

```

// stack allocated
{
   MyClass c;
   // use c
} // when c goes out of scope c is destroyed

// dynamically allocated, std::auto_ptr
{
   std::auto_ptr<MyClass> ptr( new MyClass );
   //... 
} // When ptr goes out of scope, auto_ptr's destructor releases acquired memory

```

But you must know the real scope (life-time) of the object, and also that auto_ptr's don't quite mix with standard containers.

---

### Post by jim_24601 on 2008-07-16
```

s/don't quite mix with/are deliberately and specifically designed to break, hard, if you try to put them in/
```

---

### Post by ceclauson on 2008-07-16
Thanks for your replies.

The algorithm will generate a GUI based on an XML DOM Document.  Because it's not possible to know at compile time what objects will be created, using a container seems like it's the best choice.

The objects that will be created will either be of a class that derives from a widget class, or it will be an event handler, of a class that is unrelated to the widget class.  This is why I was interested in a single container that could hold unrelated objects.

I'm thinking based on your replies that my best option is to have two lists, one for the widgets and one for the event handlers, but if anyone thinks there's a better design option, I'd be all ears.

Also, just so I understand correctly, from the replies above, I'm gathering that if delete is given a pointer whose static type is a superclass of the dynamic type of the object it refers to, it will be able to determine the dynamic type and delete it correctly, i.e., if a pass it a widget pointer, it will know that it is actually a button and handle it right.  This is kind of implied by what was said, but I just wanted to make sure explicitly.

Thanks so much for your help,
Cooper

---

### Post by dribeas on 2008-07-17
> **ceclauson said:**
> 
Also, just so I understand correctly, from the replies above, I'm gathering that if delete is given a pointer whose static type is a superclass of the dynamic type of the object it refers to, it will be able to determine the dynamic type and delete it correctly

No, but should be. There is a (not language enforced, but common usage) rule that states that any class that is meant to be derived should have a virtual public destructor [1]. Whenever you call delete on a pointer it will call the destructor of that class, that should be virtual. Dynamic binding will follow all the hierarchy to the most derived object and that destructor will be called. I would bet on it, but check that Widget destructor is defined virtual. Of course, not being forced by the language implies that you should check it.

   David

[1]: The other 'sane' option is defining the destructor as protected non-virtual for the strange case where you will never want to delete through a base's pointer. Being protected allows derived classes to be deleted and call on the parents destructor while inhibiting deletions from any other code.

The company I work for has a clear rule on this: always public and virtual destructor (whether the class was initially meant to be derived or not, the small extra cost is assumed to be worth the benefit of not running into strange bugs if later on the class is modified to be derived)

---

### Post by lisati on 2008-07-17
> **ceclauson said:**
> 

I'm thinking based on your replies that my best option is to have two lists, one for the widgets and one for the event handlers, but if anyone thinks there's a better design option, I'd be all ears.



One important thing to keep in mind is that when you (or someone else) come back to the project in a year's time, you should be able to form a clear picture of what the program's doing and what kind of data to expect in a particular variable/container/.....

---

