---
title: "Pointers - What's the Point?"
date: 2009-03-28
forum: Programming Talk
---

### Post by JordyD on 2009-03-28
First off, I'm not here to bash pointers or any silly thing like that. It's an honest question. I'm currently learning C++, but I cannot see any point to pointers.

I understand how they work, but I can't see any reason for using them. For example, a website, teaching C++ ([http://cplusplus.com/]("http://cplusplus.com/")), gave me this:

```
// virtual members
#include <iostream>
using namespace std;

class CPolygon {
  protected:
    int width, height;
  public:
    void set_values (int a, int b)
      { width=a; height=b; }
    virtual int area ()
      { return (0); }
  };

class CRectangle: public CPolygon {
  public:
    int area ()
      { return (width * height); }
  };

class CTriangle: public CPolygon {
  public:
    int area ()
      { return (width * height / 2); }
  };

int main () {
  CRectangle rect;
  CTriangle trgl;
  CPolygon poly;
  CPolygon * ppoly1 = &rect;
  CPolygon * ppoly2 = &trgl;
  CPolygon * ppoly3 = &poly;
  ppoly1->set_values (4,5);
  ppoly2->set_values (4,5);
  ppoly3->set_values (4,5);
  cout << ppoly1->area() << endl;
  cout << ppoly2->area() << endl;
  cout << ppoly3->area() << endl;
  return 0;
}

```

Which I easily rewrote, without pointers, to this:

```
#include <iostream>
using namespace std;

class CPolygon {
        protected:
                int width, height;
        public:
                void set_values (int a, int b)
                        {width = a; height = b;}
                virtual int area()
                        {return(0);}
};

class CRectangle: public CPolygon {
        public:
                int area()
                        {return(width * height);}
};

class CTriangle: public CPolygon {
        public:
                int area()
                        {return(width * height / 2);}
};

int main() {
        CRectangle rect;
        CTriangle trgl;
        CPolygon poly;
        rect.set_values(4,5);
        trgl.set_values(4,5);
        poly.set_values(4,5);
        cout << rect.area() << endl;
        cout << trgl.area() << endl;
        cout << poly.area() << endl;
        return 0;
}

```

It compiles and gives the same result.

Is there some pointer to pointers that I'm missing? Every example of pointers I see I can't help but thinking, "Why not just use the variable itself?"

If anybody could explain the point to pointers, I would greatly appreciate it.

Thanks,
Jordy

---

### Post by stroyan on 2009-03-28
Pointers are able to point to data that is allocated and released as needed.
The new and delete functions create and release data structures.
Since allocated data structures can contain pointers they can be
arranged into chains or trees.
A program can use that to react to varying events or inputs.

---

### Post by JordyD on 2009-03-28
> **stroyan said:**
> Pointers are able to point to data that is allocated and released as needed.
The new and delete functions create and release data structures.
Since allocated data structures can contain pointers they can be
arranged into chains or trees.
A program can use that to react to varying events or inputs.

Could you give me an example?

---

### Post by sujoy on 2009-03-28
say you dont know how long an array you need. so you take in the length as input from user at runtime and allocate memory at runtime.

```


int main()
{
    int *arr, size;
    scanf ("%d",&size);
    arr = (int *) malloc (sizeof(int) * size); /* allocate memory dynamically */
    /* do stuffs with the array
    free (arr) /* release the memory */
    return 0;
}
```

---

### Post by c174 on 2009-03-28
Pointers are for dynamic memory and morphology, and also for referencing already existing objects. For example, extending the code you gave

```

int main(...) {

   int answer;
   cout << "Do you want to create a rectangle (1) or a triangle (2)" << endl;
   cin >> answer;

   // create a pointer to a polygon
   CPolygon* polygon = 0;

   switch( answer ) {
   case 1:
      polygon = new CRectangle();
      break;
   case 2:
      polygon = new CTriangle();
      break;
   default:
      // dont create anything
      break;
   }

   // more stuff...

}

```

As you can see "polygon" is used to store the adress of memory allocated at run-time. Also, a "polygon" can point to different types - if they inherint from "CPolygon". Just keep working on the tutorials, it will all come... :)

---

### Post by crazyfuturamanoob on 2009-03-28
When you call a function, the arguments get copied in the stack. So if you change an argument from a function, the original value doesn't change. 

There is a 500Mb database, and a function to handle it. If you use pointer instead of the variable itself, you save lots of time when that 500Mb isn't being copied anywhere (just the 4 bytes a pointer needs).


And if you use pass the database itself, not pointer, the function can't do necessary changes to the database, because the original variables don't change. 

Of course, you could make the function to return a new database, but again, copying 500Mb around will take time.


Also, how do you think dynamically linked lists could work without pointers?

---

### Post by eye208 on 2009-03-28
> **crazyfuturamanoob said:**
> When you call a function, the arguments get copied in the stack. So if you change an argument from a function, the original value doesn't change.
Pointers should never be passed between functions.

Why not?

Because as soon as there are two or more pointers pointing at the same object, you run a risk of deallocating the object multiple times (=crash) or not at all (=memory leak).

Pointers should always be wrapped in container classes. The container "owns" the pointer, i.e. it is responsible for deallocating the object. Deallocation typically takes place in the container's destructor function. This is the only way to make code exception-safe because the destructor will be called automatically.

If you have to make the same object accessible at multiple places in a program, use a container that implements reference counting, e.g. shared_ptr/weak_ptr from the Boost library. This will ensure automatic deallocation as soon as the last reference to the object runs out of scope.

---

### Post by DGortze380 on 2009-03-29
take a look at link lists.

pointers are simply variables that hold memory locations, they have various uses in c++, linked lists being one of them, dynamic memory allocation being another.

---

### Post by CptPicard on 2009-03-29
IMO the simplest way to understand in general the need for some kind of reference type that has reference instead of value semantics is to consider a really simple example like this... think of a data object A which needs to know about another data object B. In this case you could just nest B inside A as a value. But what if B needs to also know about A? By same logic, B would contain A which would contain B which would... be an infinitely large structure.

The solution is to use a reference type, which is a (boundedly) small value that knows "how to get" its referent. This way both A and B hold a reference (in C terms, pointer -- the C++ reference is a more specific issue).

Also, consider:

```

X = SomeObject()
Y = X

```

Now, if we operate under value semantics, Y is actually a copy of its own of the object we constructed. If you for example store Y somewhere, it is a whole different SomeObject from the one that is X. If you make changes to Y, they are not visible via X. If we have reference semantics, both X and Y are the *same* SomeObject. X.alter() will produce a change visible via Y.

As a last matter, pointers specifically of course have a fundamental hardware meaning as containing a memory address. The fact that we have addressable RAM that can contain addresses to within itself is essentially what enables the existence of data that is structured like this in the first place.

---

### Post by nvteighen on 2009-03-29
You dared to challenge the power of the Allmighty Pointer? Prepare to die!! :)

Ok, let me see. A pointer is always needed when you need to have access to some memory through different names no matter where you're located. Think of them as symlink files in Linux and you'll understand what I mean.

Sometimes you just need to change some memory section but you have no proper access to it because you're in stack frame A and your value is in stack frame B. You can't access it directly, so you need a pointer in frame A that points to that value in frame B.

As you surely know, dynamic allocation uses a special "frame" that's never destroyed until the application exits: the heap. But the heap is not part of the stack, so you'll always need a pointer because in code you're never "in heap". But as you see, the base idea remains the same.

As a result, what you get are global variables with selective scope. Or better said, the ability to extend a certain local variable's scope by referring to it from its outside.

That's the most extended use of pointers. To use a pointer to reference a variable in the same frame as in your example is pointless, of course. And also, this is just needed when your language is low-level... in other levels of abstractions, you just get rid of pointers because you start talking about objects and not about "memory locations that happen to be considered as objects"... but that's another story.

---

### Post by ZuLuuuuuu on 2009-03-29
> **eye208 said:**
> Pointers should never be passed between functions.

Why not?

Because as soon as there are two or more pointers pointing at the same object, you run a risk of deallocating the object multiple times (=crash) or not at all (=memory leak).

How does passing pointers between functions create multiple references to the same data?

---

### Post by Reiger on 2009-03-29
Because the pointer itself is copied, i.e. passed by value to the function.

That is if you do a function call foo(a,b), the data referred to by both a and b in their current scope is/must-be copied on top of the existing stack. With litteral values this is never a problem, because when you exit the function-subroutine the part of the stack that used to hold these copy values is effectively destroyed by changing the stack-pointer (or the combination of variables that instruct the CPU at what instruction it should resume code execution of the application, rather than internal house-keeping routines) to "back to whence it came". However, pointers have different semantics from litteral values - and so the copy behaviour results in side effects (see why advances in Pure Functional Programming and Transactional IO are such blessings to modern software development?)

Therefore, consider (pseudo- C++):
[php]
foo (*some_pointer);

foo (*a) { /*within *this scope* (stack frame) we now have 2 copies of the reference to what_ever *a points to: namely *a in this/current scope and some_pointer of the outer scope */
  bar(*a); }

bar(*b) {
/* within *this* scope (stack frame) we now have 3 copies of the reference to what_ever *b points to: namely *a in foo(), *b in this/current scope, and *some_pointer of the outer scope */
}[/php]

So if bar() were for instance to de-allocate memory pointed to by *b; any subsequent call foo(some_pointer) will cause app-crash: because bar has essentially renderd some_pointer to stale data and therefore upset the internal consistency of the program. And so would memory access through *a in foo() after the call to bar();

---

### Post by ZuLuuuuuu on 2009-03-29
> **Reiger said:**
> [php]
foo (*some_pointer);

foo (*a) { /*within *this scope* (stack frame) we now have 2 copies of the reference to what_ever *a points to: namely *a in this/current scope and some_pointer of the outer scope */
  bar(*a); }[/php]

Because you cannot see the outer pointers (except if it is global), basically you have only 1 pointer at a time to the same data. Not 2 or 3 pointers.

> So if bar() were for instance to de-allocate memory pointed to by *b; any subsequent call foo(some_pointer) will cause app-crash: because bar has essentially renderd some_pointer to stale data and therefore upset the internal consistency of the program.

If you try to use a pointer after deallocating its memory then it is your problem I guess :) And If you have more than 1 destroying function for same kind of data (which may cause some issues you mentioned) then you should consider refactoring your design.

---

### Post by Reiger on 2009-03-29
> **ZuLuuuuuu said:**
> Because you cannot see the outer pointers (except if it is global), basically you have only 1 pointer at a time to the same data. Not 2 or 3 pointers.

No, perhaps I should make myself more clear. If we just consider the simple-variable semantics:
[php]
int myVar = 42;

foo(myVar);


foo(int myArg) {
 myArg++;
}
[/php]

How many copies of myVar have been created in total once you execute myArg++ ?

Please note: at this point *both* myVar and the myArg are still in the memory. Indeed they must *both* be because myVar = 42 is the last code that is executed, and so the first code after that statement, within that scope should be our point-of-return from the function foo(). So we cannot be sure that we can already discard myVar -- it would make for some pretty weird behaviour if subsequent statements would want to use myVar, right? 

We do, therefore, have copies of the function argument as long as we are within foo(). Once we are out of that function we don't (unless we were to return the argument!), but it is up to the programmer to realise this caveat. If the function arguments are pointers, you see that this can make explicit memory management a good bit more difficult. Consider, for instance the case where you are passing pointers to objects with member fields. Those member fields (in this raw-pointer-access-design) may or may not have been set or unset using prior acces-by-pointers... How can a function know? 

Also for an interesting comparison: old PHP (4) tutorials will often include a lot of explicit memory management in functions interfacing with libraries (I'm looking at you, gd!), because PHP too works with pointers. (&$var is a pointer to $var). And a lot of the standard functions are actually straight from C (some type coercion is implictly performed, of course). You had to call destructors on library objects explictly for fear of creating memory leaks within your PHP apps.

I entirely agree that having multiple functions destroy the same data or parts of the same data is asking for trouble. However, this need for 'refactoring your design' is essentially what the earlier post about a 'container object' addresses. ;) (And solves the problem of how a function is to know: it doesn't because it doesn't do raw-pointer-access. Instead is uses member functions of the container object which can keep track of its internal state.)

---

### Post by c174 on 2009-03-29
> **eye208 said:**
> Pointers should never be passed between functions.

Where did that rule/style guide for C++ programming come from?? Look at any library in C or C++ and you will see a lot of passing of pointers in function calls. It is a VERY normal thing to do.

---

### Post by nvteighen on 2009-03-29
> **c174 said:**
> Where did that rule/style guide for C++ programming come from?? Look at any library in C or C++ and you will see a lot of passing of pointers in function calls. It is a VERY normal thing to do.
It is normal, but not optimal unless you use **const** pointers. eye208 is right: you can easily create a memory leak. And you can end up with several references to the same object.

Of course, both should be avoided by clear design and careful coding...

---

### Post by eye208 on 2009-03-30
> **c174 said:**
> Where did that rule/style guide for C++ programming come from??
From the inventor of the language.

[http://en.wikipedia.org/wiki/Resource_Acquisition_Is_Initialization](http://en.wikipedia.org/wiki/Resource_Acquisition_Is_Initialization)

---

### Post by c174 on 2009-03-30
> It is normal, but not optimal unless you use const pointers. eye208 is right: you can easily create a memory leak. And you can end up with several references to the same object.

I agree. However, a C++ library such as wxWidgets is passing pointers "the bad way", and you have to read the docs to know how it manages memory.

> From the inventor of the language.

[http://en.wikipedia.org/wiki/Resourc...Initialization](http://en.wikipedia.org/wiki/Resourc...Initialization)

Yeah, well... When a pointer e.g. (MyClass* some_var) goes out of scope the destructor ~MyClass is not called. So I don't think the RAII-concept is relevant here (There will only be a problem if the memory is never freed or freed multiple times. Of course wrapping pointers in classes is a good way to achieve memory-management due to RAII :) )

I think the OP should experiment with pointers in all ways, to get to know the possibilities and pitfalls. That's what I was aiming at in my earlier post.

---

### Post by eye208 on 2009-03-31
> **c174 said:**
> I agree. However, a C++ library such as wxWidgets is passing pointers "the bad way", and you have to read the docs to know how it manages memory.
wxWidgets 2.9 includes wxSharedPtr, a reference-counting smart pointer template similar to Boost's shared_ptr. It also includes the wxWeakRef container for GUI object pointers.

GUI object pointers (such as wxWindow*) are special in wxWidgets because they are owned by wxApp. So you don't have to worry about deleting them. However, you do have to worry about accessing a wxWindow which has been deleted somewhere else. That's why wxWindow pointers should be wrapped in wxWeakRef containers.

You can see that the wxWidgets developers are aware of the problems, and addressing them. Pointers are the only types for which RAII doesn't work. Whenever a pointer is aquired (from *new* or some C library function), it should be wrapped in an appropriate container immediately.

---

### Post by c174 on 2009-03-31
> **eye208 said:**
> wxWidgets 2.9 includes wxSharedPtr, a reference-counting smart pointer template similar to Boost's shared_ptr. It also includes the wxWeakRef container for GUI object pointers.

I guess they kept raw pointers like wxWindow* because it is more handy when you create new widgets by deriving existing ones. Maybe that can be wrapped in a nice way too, but so far it is not I guess? (I'm still in wxWidgets 2.8 )

Yes, I also think pointers should be wrapped. But often they are not, even in C++.

---

### Post by eye208 on 2009-04-01
> **c174 said:**
> Yes, I also think pointers should be wrapped. But often they are not, even in C++.
That's because many C++ programmers are in fact C programmers. They changed their compilers but not their mindsets.

---

### Post by Garratt on 2009-04-01
> **crazyfuturamanoob said:**
> When you call a function, the arguments get copied in the stack. So if you change an argument from a function, the original value doesn't change. 

There is a 500Mb database, and a function to handle it. If you use pointer instead of the variable itself, you save lots of time when that 500Mb isn't being copied anywhere (just the 4 bytes a pointer needs).


And if you use pass the database itself, not pointer, the function can't do necessary changes to the database, because the original variables don't change. 

Of course, you could make the function to return a new database, but again, copying 500Mb around will take time.


Also, how do you think dynamically linked lists could work without pointers?

That's the correct answer...! i was just about to reply and say the same thing.

Edit: woops. helps to read the page count before posting

---

### Post by Gordon Bennett on 2009-04-01
What's next - the point of the wheel?

---

### Post by nvteighen on 2009-04-01
> **Gordon Bennett said:**
> What's next - the point of the wheel?
Wheels are pointless... they're circular :)

---

### Post by WitchCraft on 2009-04-01
The point of pointers is to point to something.

e.g. you have a function in an executable where you don't have the source of.

let's assume the function is

bool ValidateKey(char* szKey)

Now assume the executable is a 30 day evaluation version.

You can now define a pointer to ValidateKey

bool (*ValidateKey_0wn3d)(char*) ;

now you can copy a brute-force char* generating function in a shared library, LD_PRELOAD/inject this library and let an infinite loop validate all random char* sequences. 
All you need to do is to say:  ValidateKey_0wn3d = 0xOFFSET

If one of them returns true, output the sequence to stdout/file.


another point of pointers is to point to sequences:
e.g. "abcdefghijklmnopqrstuvwxyz"
so you define a char pointer to "abc..." and you can iterate through the sequence in a for loop.
In other words, a pointer is (the starting address of) an array.

Just that a pointer is (conceptionally) more then an array, although it basically is (physically) less than an array.

---

### Post by JordyD on 2009-04-02
Thanks for all the responses. They helped. :)

Does anybody know how to mark the thread as solved? It's not anywhere in the 'Thread Tools' dropdown.

---

### Post by Peasantoid on 2009-04-02
One of the many uses of pointers is returning by reference. Suppose you have a function that returns multiple ints, not just one:
```
void setInts(int *ptr1, int *ptr2) {
    *ptr1 = 1;
    *ptr2 = 2;
}

int main(int argc, char *argv[]) {
    int num1, num2;
    num1 = num2 = 0;
    setInts(&num1, &num2);
    /*
        num1 now equals 1
        num2 now equals 2
    */
    return 0;
}
```
The mark-as-solved thing doesn't exist anymore, but you can add a "solved" tag.

---

### Post by eye208 on 2009-04-03
> **Peasantoid said:**
> One of the many uses of pointers is returning by reference.
In C++ you would use references instead of pointers:
```
void setInts(int &n1, int &n2) {
    n1 = 1;
    n2 = 2;
}

int main(int argc, char *argv[]) {
    int num1, num2;
    num1 = num2 = 0;
    setInts(num1, num2);
    /*
        num1 now equals 1
        num2 now equals 2
    */
    return 0;
}
```
Advantage: There are no dereference operators (* or ->) in the function body and no address-of operators in the function call. The function declaration alone determines whether it is call-by-value or call-by-reference. You can switch from one to the other without changing the rest of the code.

---

### Post by JordyD on 2009-04-11
> **sujoy said:**
> say you dont know how long an array you need. so you take in the length as input from user at runtime and allocate memory at runtime.

```


int main()
{
    int *arr, size;
    scanf ("%d",&size);
    arr = (int *) malloc (sizeof(int) * size); /* allocate memory dynamically */
    /* do stuffs with the array
    free (arr) /* release the memory */
    return 0;
}
```

Can this be done in C++ using cin? I'm not very familiar with scanf(). Is it usable with C++?

Thanks,
Jordy

---

### Post by slavik on 2009-04-11
> **JordyD said:**
> Can this be done in C++ using cin? I'm not very familiar with scanf(). Is it usable with C++?

Thanks,
Jordy
yes.

Please see google for details. Your question shows little research into the matter. It may be a more advanced topic than you are ready to take on.

---

### Post by theDaveTheRave on 2009-04-14
Hi all,

I've read this thread with considerable interest, I am a JAVA programmer (well novice / learning to be better!). And I am being "forced" to learn some C at my university (for a Masters course).

Well I have a real headache when it comes to pointers.

I persistently want to write things in an "object oriented" fashion.

So I end up writing code to create a <struct> that holds the references to the various "variables", then insert getter and setter methods to those variables.

This seems to work? am I working in a "sensible" fashion?

As I declare all my variables as "pointers" (including the <struct> "objects" that I create), and then use a "constructor" in the main method, or wherever else I need to call into creation a particular type of struct object. I guess that when my <struct> goes out of scope (when the program terminates) it will automatically be destroyed, but I have a feeling I should "destroy" it manually just to be sure. Please note I am only creating really small "projects" that take an input and spit out an output, then the program closes.

I'm not sure however if this is sensible / easier to read or what.

I would just like to know if I continue in this method if I will come unstuck later on?

thanks for the advice.

David

---

### Post by slavik on 2009-04-14
> **theDaveTheRave said:**
> Hi all,

I've read this thread with considerable interest, I am a JAVA programmer (well novice / learning to be better!). And I am being "forced" to learn some C at my university (for a Masters course).

Well I have a real headache when it comes to pointers.

I persistently want to write things in an "object oriented" fashion.

So I end up writing code to create a <struct> that holds the references to the various "variables", then insert getter and setter methods to those variables.

This seems to work? am I working in a "sensible" fashion?

As I declare all my variables as "pointers" (including the <struct> "objects" that I create), and then use a "constructor" in the main method, or wherever else I need to call into creation a particular type of struct object. I guess that when my <struct> goes out of scope (when the program terminates) it will automatically be destroyed, but I have a feeling I should "destroy" it manually just to be sure. Please note I am only creating really small "projects" that take an input and spit out an output, then the program closes.

I'm not sure however if this is sensible / easier to read or what.

I would just like to know if I continue in this method if I will come unstuck later on?

thanks for the advice.

David
your problem is much deeper than that. You need to learn to think in other ways. Knowing only one language and only one way of thinking makes you a crappy developer.

But i don't know anything ... I just support crappy code (and infrastructure) others write.

---

### Post by theDaveTheRave on 2009-04-14
> **slavik said:**
> your problem is much deeper than that.

I had a feeling that may be the case :cry: 

>  You need to learn to think in other ways. Knowing only one language and only one way of thinking makes you a crappy developer.

OOh thanks, not sure I appreciate that.....

> 
But i don't know anything ... I just support crappy code (and infrastructure) others write.

Oh OK fair enough, no offence taken then. :lolflag:

In all honesty I like the idea of keeping data "abstracted" away and protected from interference, which is probably why I keep falling back on the "object oriented" way of doing things.

It also seems cleaner to me, easier to document, and easier to understand, but like you say >  I don't know anything 

I have been spending a lot of time recently reading other peoples code. I find myself thinking a lot along the lines of
> but if you put that bit of code in a separate file you wouldn't have to re-write it all over the place, you could just call "the" function that lives in "that" class and takes "this" type of data structure, and then perform "the" function on it.

In essence my code ends up with lots of files with relatively small amounts of code, but each file is easily transported to another project, if I need it elsewhere..... typical of how I write stuff in Java and in C

oh and your comment of
> 
Knowing only one language and only one way of thinking
I know exactly where you are coming from, being a bilingual brit living in Paris :lolflag:
Knowing the extra methods is very powerfull. I guess it is like learning anything new, it takes time and effort to really get to grips and feel that you are fully "fluent" in the new language, and you have all that extra bagage of "but I do it like that in blah blah blah language"

I think I need to start teaching the 8 month old twins to program in  Java, PHP, C and perl.... just for good measure!

David

---

### Post by Arndt on 2009-04-14
> **theDaveTheRave said:**
> Hi all,

I've read this thread with considerable interest, I am a JAVA programmer (well novice / learning to be better!). And I am being "forced" to learn some C at my university (for a Masters course).

Well I have a real headache when it comes to pointers.

I persistently want to write things in an "object oriented" fashion.

So I end up writing code to create a <struct> that holds the references to the various "variables", then insert getter and setter methods to those variables.

This seems to work? am I working in a "sensible" fashion?


If you have a complex data structure which one part of your code knows everything about, and the rest of your code should be able to access and use, but otherwise know very little about, that's a reasonable approach.

One way of doing this is with macros, which are not frowned upon in C.

You encapsulate data in structs in C, just as in C++ or Java, and you write functions to allocate memory for struct instances, and functions for freeing the memory again, but that's usually where the "object orientation" stops.

It doesn't mean that all data traversal needs to be expressed in the fundamental steps of the language. For example, a linked list can be traversed by following 'next' pointers explicitly, and that's quite usual, but if you have many kind of structures, you can program an iterator abstraction yourself which makes the traversal cleaner.

If you want to write a whole object orientation framework, you can do that. It's been done for example to handle graphical user interfaces, where there are object hierarchies. But I think only a quite large project has a use for that.

> 
As I declare all my variables as "pointers" (including the <struct> "objects" that I create), and then use a "constructor" in the main method, or wherever else I need to call into creation a particular type of struct object. I guess that when my <struct> goes out of scope (when the program terminates) it will automatically be destroyed, but I have a feeling I should "destroy" it manually just to be sure. Please note I am only creating really small "projects" that take an input and spit out an output, then the program closes.

David

When the program ends, all memory it has allocated goes back to the system (whether written in C or something else). For debugging purposes, it may be a good idea to explicitly free everything.

While the program is running, however, C does no deallocation at all for you, with the exception of what's on the stack, and you shouldn't put much there. Specifically, no "destructors" are run.

I don't really know how to lead the way conceptually from object orientation to C programming, but with your small projects, look at them from a high level, and see which of the access functions you write are really used, and if you have built any unnecessary detours into the program. If you can cut off unnecessary structures and code, you're probably getting closer to the C way of doing things (even if it feels like totally ruining the OO approach).

There are function pointers in C, and you can easily get the effect of doing a function call, where the actual code being run is determined by data, it's just not done all the time.

---

### Post by CptPicard on 2009-04-14
My C is full of "object-structs" that also contain pointers to "methods" that take a pointer to that said struct. That way, you can override even on per-object basis a bit like in Python. Nothing wrong with that kind of approach, it often arises quite naturally.

---

### Post by slavik on 2009-04-14
Thing is, thinking in OO is not the problem, but when you can only think in OO, that's the problem.

Abstraction adds inefficiency, which is what you sometimes you need ... raw optimization. :) sometimes you want to even get rid of a function call to speed things up just a little. ;)

---

### Post by nvteighen on 2009-04-14
> **theDaveTheRave said:**
> 
So I end up writing code to create a <struct> that holds the references to the various "variables", then insert getter and setter methods to those variables.

This seems to work? am I working in a "sensible" fashion?

As I declare all my variables as "pointers" (including the <struct> "objects" that I create), and then use a "constructor" in the main method, or wherever else I need to call into creation a particular type of struct object. I guess that when my <struct> goes out of scope (when the program terminates) it will automatically be destroyed, but I have a feeling I should "destroy" it manually just to be sure. Please note I am only creating really small "projects" that take an input and spit out an output, then the program closes.


If you take a look on how GTK+ works, you'll see it works exactly as you're doing... :) Moreover, the C Standard Library does it too when it comes to files (FILE *... and all the f*() functions, which are methods. fopen() is the constructor and fclose() the destructor).

It's a very natural solution: Object-Orientation is a programming paradigm, not a syntax feature... So, no matter if you have a native syntax to make OOP explicit (as C++, Java, Python, Ruby, Smalltalk, etc. do): what matters is the concept. If you abstract stuff not in procedures but in objects, then you are in OOP.

But I agree with slavik: OOP is not the ultimate solution. You should learn other paradigms (e.g. procedural-structured, functional... and why not logic and declarative programming?).

---

### Post by theDaveTheRave on 2009-04-16
> **nvteighen said:**
> If you take a look on how GTK+ works, you'll see it works exactly as you're doing... :) Moreover, the C Standard Library does it too when it comes to files (FILE *... and all the f*() functions, which are methods. fopen() is the constructor and fclose() the destructor).


Ah I feel much better now #-o



> **nvteighen said:**
> 
 You should learn other paradigms (e.g. procedural-structured, functional... and why not logic and declarative programming?).

Hmm?? aren't all computer programs "logic" based?? ;)

as for procedural.... I allways thought that the anything that was in OOP form could be re-written in a "procedural" layout.... but will just use up more lines of code as you re-use certain code structures.... hence the whole point of abstracting out functions.

Slavic you mention that
> 
Abstraction adds inefficiency, which is what you sometimes you need ... raw optimization.  sometimes you want to even get rid of a function call to speed things up just a little.

Surely if I abstract out a function that only get called once or twice it will only ever come into "scope" of the program when it is called, surely that is more eficient then writing it into the code whenever you need it.... Although as I write this I think I'm understanding where you are coming from.... 

The joy of the ubuntu forums, I love em....

Now can anyone tell me if the coffee is ready   ;)

David

---

### Post by nvteighen on 2009-04-16
> **theDaveTheRave said:**
> 
Hmm?? aren't all computer programs "logic" based?? ;)

Logical programming is a paradigm: Look at Prolog in Wikipedia for more information. Declarative programming is actually much more common than people believe... HTML is a case (you just describe what there is) :)

> 
as for procedural.... I allways thought that the anything that was in OOP form could be re-written in a "procedural" layout.... but will just use up more lines of code as you re-use certain code structures.... hence the whole point of abstracting out functions.

Wait a bit, what do you mean by rewriting into procedural? If you mean to effectively translating a model of object-relationships (OOP) into a model of procedure-sequences (procedural), then I have to disagree with you: if the project is large enough, you'll probably ending up either writing really long and unmantainable code or you'll reimplement some sort of ad hoc OOP behind the scenes. In the other hand, if you mean "rewriting into procedural" means taking away an OOP-aware syntax and using a procedural syntax... then you're just taking away the syntax features, but you'll still be working in OOP. 

For example, when using GTK+, in no matter what language, you'll see how all your code will be object-centered: you'll be always dealing with the relationships between objects in order to get something working. When you write **gtk_window_show(GTK_WINDOW(myWindow));** in C, you're still centered on an object and saying that there's some action that ·belongs" to myWindow just because it is meant to be a GtkWindow... What is the difference of that with PyGtk's **myWindow.show()**? Just nicer syntax. As a contrast, in ncurses, which serves for a similar purpose, you usually deal with a set of processes (the "window" abstraction is too weird...). 

> 
Surely if I abstract out a function that only get called once or twice it will only ever come into "scope" of the program when it is called, surely that is more eficient then writing it into the code whenever you need it.... Although as I write this I think I'm understanding where you are coming from.... 


Hm... in C you could use inline functions... These get copied into the assembly code instead of using a call to them and therefore speeding things up but saving yourself from a mantainance hell. But, I've heard there's a point where inlines just don't work anymore because the compiler can't copy the code accurately (for example, when using optimization flags)... Can someone please confirm this?

---

### Post by CptPicard on 2009-04-16
> **theDaveTheRave said:**
> 
I think I need to start teaching the 8 month old twins to program in  Java, PHP, C and perl.... just for good measure!


Except perl, those are too similar. Imperative programming and OOP as its extension essentially "think" in fundamentally same ways, although OOP emphasizes datatype hierarchies and combines a method call dispatching system to that hierarchy -- in ways which I am not all that sure I am 100% in agreement with... "Computation in the Kingdom of Nouns" is good essay on this, and CLOS-like multiple-dispatch OOP systems that decouple functions from objects, but are still able to resolve them correctly according to parameter type, are much more flexible and free you a lot from the design pattern hell.

Teach the twins Scheme instead, it's syntactically trivial but remarkably expressive -- conceptually all-encompassing if you want it to be really.

---

### Post by Can+~ on 2009-04-16
I think you're mixing Procedural with Imperative.

[http://www.ingesmart.cl/fborquez/ILI-253/doc/cl1.pdf](http://www.ingesmart.cl/fborquez/ILI-253/doc/cl1.pdf)

Read that document about paradigms, it will make things so much clear.

---

### Post by CptPicard on 2009-04-16
Ok, "procedural" maybe would have fit there better. But procedural programming typically adds the concept of "procedure" on top of a fundamentally imperative style (in contrast to functional programming where the "procedure" is a typically declaratively-specified function). For me one of the biggest, most meaningful distinctions has always been imperativeness and side-effects to state vs. declarativeness and things like pure-functionality... so there is a certain reason as to why I said what I did, but ... I concede a point ;)

---

### Post by theDaveTheRave on 2009-04-17
> **Can+~ said:**
> I think you're mixing Procedural with Imperative.

[http://www.ingesmart.cl/fborquez/ILI-253/doc/cl1.pdf](http://www.ingesmart.cl/fborquez/ILI-253/doc/cl1.pdf)

Read that document about paradigms, it will make things so much clear.

WOW

Brilliant document, great link.

I would recomend this to everyone. In fact as and when I get my own web site I'm going to ensure I link in to the authors site.

In case anyone is interested, I certainly was so as I can use the reference, here are the authors other pages on his ftp site
[http://www.ingesmart.cl/fborquez/]("http://www.ingesmart.cl/fborquez/").

I hope other find this stuff equally interesting......

back on topic....

I think I better understand where I have been going wrong. I do seem to think in a more "object oriented" manner, and I seem to struggle to think in other "modes".

I find the coding in C is too long and often feels convoluted, and hard to read, then I find I can acheive the same result in half the time in java - but that may simply be I'm more used to the OO methodology, and have a better grasp of the libraries available to me.

Talking of which, I'm sure that everything I do in Java I can do in C? But I seem unable to locate the equivalent of the API for C, this may in fact help me to understand better what I can do, and how to do it!

If anyone link me to the core API for C (or it's equivalent) I will be truly gratefull. This seems to be something that I and some of my college buddies have missed - 

Ok scrub that I've just found them by searching for the C standard library <doh>

thanks again to everyone here.

David

---

### Post by eye208 on 2009-04-17
> **theDaveTheRave said:**
> Talking of which, I'm sure that everything I do in Java I can do in C? But I seem unable to locate the equivalent of the API for C, this may in fact help me to understand better what I can do, and how to do it!
C comes with a portable runtime environment called "GNU/Linux".

Open Synaptic and search for packages beginning with "lib". These are the class libraries of C. To find the SDK, search for packages ending with "-dev".

---

### Post by Can+~ on 2009-04-17
> **theDaveTheRave said:**
> WOW

Brilliant document, great link.

I would recomend this to everyone. In fact as and when I get my own web site I'm going to ensure I link in to the authors site.

In case anyone is interested, I certainly was so as I can use the reference, here are the authors other pages on his ftp site
[http://www.ingesmart.cl/fborquez/]("http://www.ingesmart.cl/fborquez/").

Actually, the authors were the developers of Leda, a language that eventually, disappeared:

[http://web.engr.oregonstate.edu/~budd/vita/ledatoc.html](http://web.engr.oregonstate.edu/~budd/vita/ledatoc.html)

The links to the documents are now dead. But you can still get to them via:

[http://web.engr.oregonstate.edu/~budd/Books/leda/info/](http://web.engr.oregonstate.edu/~budd/Books/leda/info/)

---

