---
title: "exceptions ..."
date: 2008-08-28
forum: Programming Talk
---

### Post by slavik on 2008-08-28
I don't like exceptions ...

Most people who use exceptions think of them as something special. The truth is, that it is possible to add exceptions to any language that has access to the kernel's syscall interface (kill() and signal() are what is needed), due to the simple fact that an exception is not much more than a software interrupt.

Here is a way of doing an exception in C. Please note that it won't look as pretty as a try catch block in languages that explicitly support exceptions.

the standard try-catch:
```

try {
 ... code that can throw an exception
}
catch (exception) {
 ... code to handle the exception if one has been thrown
}

```

the way it would look in C (should look like a special part of OpenGL):
```

void func(int signal) {
 exception e = getException();
 ... code to handle the exception
}

tryBegin(func);
 ... code that can raise(SIGUSR) #or some other signal you want to use for exceptions
tryEnd();

```

The library will need some wrappers ...

How will that work?
tryBegin() will have to have access to a stack of (void*) that is allocated on the heap (global to the exception library). it will then place the function pointer on top of the stack (you need a stack to allow for nested try-catch blocks). it will then call signal() to bind the new pointer as the handler for the SIGUSR signal.

the 'throwing' process calls throw(), which is a wrapper around raise(SIGUSR) which is same as kill(getpid(), SIGUSR) causing the current process to get interrupted. throw() will also set up an exception in the global namespace similar to errno, but instead of an int, it will be a struct with an errno and an error string and whatever other info you want. these will have to be arguments to throw() or another function to assemble the exception which is then given to throw() (OO, right here).

tryEnd() will remove the pointer to a handler from the top of the list and set the new top to be the handler for the signal (in effect, restoring the stack/signal state to what it was before tryBegin()).

The real reason why I don't like exceptions is that for every interrupt that fires, you have to save the CPU's registers (even if that CPU is written in C++), handle the action and then restore the registers.

trick question: an interrupt handler cannot be interrupted, because the handler disables interrupts. how can the handler exit so that interrupts are enabled after it exists, but still not get interrupted while trying to exit?

---

### Post by CptPicard on 2008-08-28
Interesting, but a bit too much of an OS-hack way to go about it... of course if you insist on doing it in C using syscalls you probably can do something like this :)

An exception is essentially a special case of continuation (an escape continuation). All you just do is just mark the stack frame where you're catching, and then implicitly pass the pointer (the continuation) as an extra parameter in your function calls. Throwing invokes the continuation, in practice just unwinding enough stack to get to do an error value "return" in the marked stack frame...

---

### Post by Sinkingships7 on 2008-08-28
Being a do-it-myself kinda guy, I've gotta say that I've always had a strong distaste towards built-in exceptions as well. Not that they aren't convenient; just that I enjoy being a masochist. What with C++ being my first (real) language and all...

*Goes back to reading his Python book & rocks back and forth*

*You're the only thing that can save me now...*

---

### Post by CptPicard on 2008-08-28
> **Sinkingships7 said:**
> Not that they aren't convenient; just that I enjoy being a masochist. What with C++ being my first (real) language and all...

Gah... why is there not a "-1" button? :)

It's true though that exceptions really suck in a language that doesn't have automated orphaned-resource collection (essentially, gc).

---

### Post by Sinkingships7 on 2008-08-28
[QUOTE=CptPicard]Gah... why is there not a "-1" button? :)[/QUOTE]
+1 :)
[QUOTE=CptPicard]It's true though that exceptions really suck in a language that doesn't have automated orphaned-resource collection (essentially, gc).[/QUOTE]
For the sake of my learning pleasure, where do the paths of garbage collection and exception-raising cross? Are built-in exceptions *part* of GC? As of right now, it seems to me that the two are unrelated - that one could exist without the other. Am I wrong?

---

### Post by CptPicard on 2008-08-28
They are unrelated certainly, but the problem is that in a language without GC, exceptions make it remarkably easy to leak memory, and code that is exception-safe in this regard is very hard to write and can become very nasty to read.

To alleviate this, the concept of RAII was developed and pointers are essentially these days often wrapped into stack-allocated holders that make sure they are deleted at stack unwind... but, this is one of those "hacks around the language" that cause you to have your signature...

---

### Post by Sinkingships7 on 2008-08-28
> **CptPicard said:**
> They are unrelated certainly, but the problem is that in a language without GC, exceptions make it remarkably easy to leak memory, and code that is exception-safe in this regard is very hard to write and can become very nasty to read.

To alleviate this, the concept of RAII was developed and pointers are essentially these days often wrapped into stack-allocated holders that make sure they are deleted at stack unwind... but, this is one of those "hacks around the language" that cause you to have your signature...

Ahh. Thanks for clearing that up for me. I was confused at first, then I read the Wikipedia page on RAII. Needless to say, I have a new-found appreciation for automated garbage collection. It's concepts like that which save a lot of bullets from entering many people's unsuspecting feet.

---

### Post by dribeas on 2008-08-28
> **slavik said:**
> I don't like exceptions ...
...
```

void func(int signal) {
 exception e = getException();
 ... code to handle the exception
}

tryBegin(func);
 ... code that can raise(SIGUSR) #or some other signal you want to use for exceptions
tryEnd();

```

I don't think that anything you can build manually will be cleaner, simpler or safer than language support for exceptions. To keep information on exceptions you resort to a global variable, which either is strongly typed and has a fixed number of fields and types, or is weakly typed (through void*) to allow any kind of exceptions and need to be casted to the real exception type.

It is not simple to come up with consistent flow mechanisms. Exceptions propagate across functions:
```

// C++ allows throwing any kind
void f() { throw std::runtime_exception( "Oops" ); }
void g()
{
	f();
	only_on_success();
}
void X::h() // Implementation of a method in a class
{
	try
	{
		g();
	}
	catch ( std::exception ex )
	{
		std::cout << "f() failed with exception: " << ex.what() << " in call from object " << this->name_ << std::endl;
	}
}

```

How would your system handle this code? The user will have to change the internals of g() so that if an exception is raised in f() then only_on_success() will not be executed.

The code that is registered to handle a signal (simulated catch) has a fixed signature, and you would need to devise an architecture so that it has access to the data inside the object (as to log the name of the instance in the sample above).

> **slavik said:**
> The real reason why I don't like exceptions is that for every interrupt that fires, you have to save the CPU's registers (even if that CPU is written in C++), handle the action and then restore the registers.

This is not required with languages supported exceptions, only with your emulation that has the added cost of a system call.

> **CptPicard said:**
> ...exceptions make it remarkably easy to leak memory, and code that is exception-safe in this regard is very hard to write and can become very nasty to read.

Leaking memory with exceptions is just as easy as with multiple return statements, which you may or may not like, but have language support. I don't agree in that exception safe code must be nasty to read, if it is well designed it can be really clean and simple, in most cases it starts with performing all possibly failing operations on temporaries and moving the results through non-failing operations at the end:

As an example:
```

X& operator=( X const & x )
{
	// Perform possibly failing operations through copy constructor call
	X tmp( x );
	// Swap (non-failing) data from tmp and current object, either std:: or handmade for the class
	std::swap( data_, x.data_ );
}

```

Usually a not failing swap should be implemented, as this is the path to simple exception guarantees.

Also note that memory is just one kind of resource you may leak, for the rest of the resources (in Java/C#) you need to write finalizers, in C++ there is one solution: RAII, so in GC languages you still need to be careful with the resources you hold (just in a smaller set of cases).

---

### Post by CptPicard on 2008-08-28
> **dribeas said:**
> 
Leaking memory with exceptions is just as easy as with multiple return statements, which you may or may not like, but have language support. 

The worst offender is the exception that is just magically thrown somewhere deeper in the call stack pretty much at any time and then propagates through your function for some upper-level catcher. At least multiple returns are pretty explicit and clearly under the control of the local function ... with exceptions you need to consider your function calls possible return points.

---

### Post by dribeas on 2008-08-28
> **Sinkingships7 said:**
> Ahh. Thanks for clearing that up for me. I was confused at first, then I read the Wikipedia page on RAII. Needless to say, I have a new-found appreciation for automated garbage collection. It's concepts like that which save a lot of bullets from entering many people's unsuspecting feet.

RAII is a really powerful concept and quite easy to grasp. In most cases you don't need to do extra effort for it, just use STL:

```

X * f()
{
	std::auto_ptr<X> ptr( new X() ); // RAII
	// operate, possible exceptions, multiple returns...
	if (error) return 0;
	return ptr.release();
}

```

In the sample code, ptr holds the memory with RAII, whenever the function exits, before the release() the memory is cleared and resources held by X freed. When release is called, ptr forgets about the memory and can be returned.

Note that class X can hold just any kind of resource: open file handlers, database connections... If ~X frees the internal resources, the code above will not leak either resources or memory.

In a garbage collected environment you will need to take care of some of the issues:

```

X f()
{
	X x = new X();
	// operate
	if ( error )
	{
		x.close(); // or free internal resources somehow
		return null;
	}
	return x;
}

```

Now you can see that a call to x.close() is required with GC. Memory don't need to be handled, but all other resources must.

@CptPicard: RAII is used to avoid having to consider all possible output paths in your code, that is as many returns/exceptions as you wish.

---

### Post by CptPicard on 2008-08-28
> **dribeas said:**
> 
Now you can see that a call to x.close() is required with GC. Memory don't need to be handled, but all other resources must.

Well, there are finalizers for objects, if you can afford to wait closing resources until gc gets to the object...

---

### Post by Sinkingships7 on 2008-08-28
> **dribeas said:**
> RAII is a really powerful concept and quite easy to grasp. In most cases you don't need to do extra effort for it, just use STL:

```

X * f()
{
	std::auto_ptr<X> ptr( new X() ); // RAII
	// operate, possible exceptions, multiple returns...
	if (error) return 0;
	return ptr.release();
}

```
I never did say that it was difficult to grasp, but that AGC is certainly a better overall solution. Not only do statements like try:catch have a stronger type-safety to them, but they also allow for more readable code, which can be vital in very large projects.

---

### Post by dribeas on 2008-08-28
> **Sinkingships7 said:**
> Ahh. Thanks for clearing that up for me. I was confused at first, then I read the Wikipedia page on RAII. Needless to say, I have a new-found appreciation for automated garbage collection. It's concepts like that which save a lot of bullets from entering many people's unsuspecting feet.

This is a long standing fight... explicit exception declarations vs. implicit exceptions... You seem to prefer explicit declarations, I don't have a strong position here. Anyway, search for discussions on it, there is no consensus, so I just use whatever the language requires (explicit in Java, implicit in C#, C++) and whatever idioms are used in that language.

---

### Post by dribeas on 2008-08-28
> **Sinkingships7 said:**
>  but they also allow for more readable code, which can be vital in very large projects.

I don't agree on readability. If you program a language, know the idioms, RAII is not harder to read, just different at the beginning. I have worked in a couple of big projects, and you hardly see any raw pointer or explicit deletion (not even in destructors).

Then again about error prone-ness (if that is legal english), if you have a class that holds a resource (database connection) in Java you must know when it is going out of scope so that you can call .close(). With RAII you just implement it in the destructor. 

You can get to a similar situation by using finalizers in either Java or C#, but there are important differences. First, you won't know when finalizers are called. Also finalizers have side effects with garbage collectors. In Java, classes with finalizers cannot be allocated in the same memory regions as regular classes. The GCs used are really fast because they just 'forget' memory regions, but you cannot forget about a class with a finalizer, you must call it. 

Note: 'forget' means that in generational garbage collectors, alive objects are copied to different regions in memory and then the whole region is considered freed, regardless of the number, size and type of the objects.

The magic is different in C#, but at any rate, they do have an impact on performance.

---

### Post by Sinkingships7 on 2008-08-28
> **dribeas said:**
> ... so I just use whatever the language requires (explicit in Java, implicit in C#, C++) and whatever idioms are used in that language.

As it should be. Not much you can do with the limitations of the language at hand. Goes with the whole "if you're going to hack around the language, you might as well be using a different language" argument.

---

### Post by pmasiar on 2008-08-28
This is interesting discussion.

It seems to support my often repeated (but never proven) anecdote that the language you learn first/use most/prefer tends to shape your thinking. So constructs which are elegant/idiomatic in that language are "good" and those what not are "bad". (Please note quotes, this is all about how different language shape our preferences/displeasure about some features, not about superiority of one language over another).

So if slavik's preferred languages, Perl and C, do not handle exceptions in elegant way (and handling them is lot of "unnecessary" code), natural striving to "beauty" makes brain to perceive them as undesirable.

In language like Python, with dynamic exceptions and GC, they are no problem, and sometimes quite elegant way to solve common problems.

> **dribeas said:**
> This is a long standing fight... explicit exception declarations vs. implicit exceptions... You seem to prefer explicit declarations, I don't have a strong position here. Anyway, search for discussions on it, there is no consensus, 

But still, position of experts who moved between languages is interesting.

Ie my "guru", Bruce Eckel (part of C++ standardization committee) said he at first liked checked exceptions of Java, because it made code samples more readable (was easier to follow code flow in exceptions). Only after programming big systems in Java he realized that checked exception look good in samples, but add noise (he used different negative verb)  in real-life program, and he prefers dynamic exceptions like in Python now.

So big part of this discussion is about personal preferences, but those preferences are formed by languages we use. It's like religion, most people just inherits it from parents ... :-)

So yet another argument to choose language you learn carefully: they will influence the way you think.

---

### Post by slavik on 2008-08-28
> **pmasiar said:**
> This is interesting discussion.

It seems to support my often repeated (but never proven) anecdote that the language you learn first/use most/prefer tends to shape your thinking. So constructs which are elegant/idiomatic in that language are "good" and those what not are "bad". (Please note quotes, this is all about how different language shape our preferences/displeasure about some features, not about superiority of one language over another).

So if slavik's preferred languages, Perl and C, do not handle exceptions in elegant way (and handling them is lot of "unnecessary" code), natural striving to "beauty" makes brain to perceive them as undesirable.

In language like Python, with dynamic exceptions and GC, they are no problem, and sometimes quite elegant way to solve common problems.



But still, position of experts who moved between languages is interesting.

Ie my "guru", Bruce Eckel (part of C++ standardization committee) said he at first liked checked exceptions of Java, because it made code samples more readable (was easier to follow code flow in exceptions). Only after programming big systems in Java he realized that checked exception look good in samples, but add noise (he used different negative verb)  in real-life program, and he prefers dynamic exceptions like in Python now.

So big part of this discussion is about personal preferences, but those preferences are formed by languages we use. It's like religion, most people just inherits it from parents ... :-)

So yet another argument to choose language you learn carefully: they will influence the way you think.

Did you know how exceptions can be done without them being built into the language? Do you know a way of efficiently implementing a garbage collector?

Liking C as much as I do and looking at features that higher level languages have, it is interesting to me how those features can be implemented in C. Would you say that it is wrong to know or think about how the Python interpreter that is written in C could have implemented some feature not built in to C?

Perl5 arrays are doubly linked circular lists, isn't that interesting to know? The leading Perl6 implementation project (Pugs) has the interpreter written in Haskell to give Perl6 the features that Larry wanted in Perl6 that are already in Haskell (lazy list evaluation among other things I can't remember off the top of my head).

If you are not concerned with how your favorite language does things and just take them for granted, then you are not much of a computer scientist. Remember the discussion about string concatenation? If there should be one obvious way to do string concatenation, why is the non-obvious way (create a list, then join) recommended more than straight string concatenation (string += string), because people know how the language works under the hood. You should know one level under what you are working at, that is the only way you can be efficient at whatever level you are working at. Would you disagree with that?

I recently started learning AJAX. Most tutorials have code similar to this for opening an XML connection:
```

try {
  var connect = new XMLHttpConnection(); the Mozilla one ...
}
catch (e) {
  try {  
    var connect = new MSXMLConnection(); whatever the IE one is ...
  }
  catch (e) {
    alert('Your browser does not support AJAX');
  }
}

```

Then I saw one tutorial that simply checked the variable using cascading if statements instead of cascading try-catch blocks ...

Anyway, the point of my post was not to say exceptions are evil, they are not. They allow you to return an error value without using the stack, because then you either have to limit the domain of what you can return or you need to make the return value bigger than it needs to be like in the case if I expect a function to return a long long long unsigned int, but an error occurs. In such a case, I would need two return values (one for success/fail status and the other for the error/value.

The point of my post was to show how exceptions can be created and that they are not all that special. If someone learned something from this, I am already happy. If not, well, you can't win them all. :)

---

### Post by snova on 2008-08-28
I don't usually like exceptions, because efficiency is always in the back of my mind. The golden rule according to me is, "Never calculate the same value twice", and the silver rule (actually a corollary) is "Don't call functions twice when you can cache the return instead".

This is augmented by the fact that in a freestanding environment, there is no exception handling code, as it's all in libsupc++ and I have little interest in trying to port it (though new and delete were simple enough).

---

### Post by CptPicard on 2008-08-28
Actually, the real golden rule is "use a better algorithm"... :)

---

### Post by pmasiar on 2008-08-28
> **slavik said:**
> Would you say that it is wrong to know or think about how the Python interpreter that is written in C could have implemented some feature not built in to C?
...
If you are not concerned with how your favorite language does things and just take them for granted, then you are not much of a computer scientist.

Of course.

It depends if I wear my CompSci hat, or my SolveItYesterday hat :-) When in hurry, I don't want to think how GC could be implemented, i want to have it and not to worry abut it.

> Remember the discussion about string concatenation? ... You should know one level under what you are working at, that is the only way you can be efficient at whatever level you are working at. Would you disagree with that?

That would be optimal, but not always possible. We are far from perfect.

-------

I was thinking not about how to implement exceptions (I remember first time reading about them - what a brilliant idea I thought, instead of GOTO). I was thinking about how language shapes our thinking about ways to solve a problem, and how non-obvious is it to overcome that influence.

---

### Post by dribeas on 2008-08-28
> **snova said:**
> I don't usually like exceptions, because efficiency is always in the back of my mind. The golden rule according to me is, "Never calculate the same value twice", and the silver rule (actually a corollary) is "Don't call functions twice when you can cache the return instead".

This is augmented by the fact that in a freestanding environment, there is no exception handling code, as it's all in libsupc++ and I have little interest in trying to port it (though new and delete were simple enough).

I don't really understand your post, in particular the part about calling the functions twice... On the other hand, what is clear is that you don't use exceptions for efficiency reasons? Exceptions have a name of being bad preformance wise. They are more expensive than return codes, that is a fact, but they are not really slow. We are using exceptions in critical systems (critical to us is 300 threads sending data packets at 50 Hz, that is each 20ms, with CORBA for a total of 15k packets per second) and all CORBA errors are handled as exceptions. The limits in the system are not due to exceptions, and that is due to the fact that exceptions are expensive when they are thrown, and not so much when errors are not produced.

This comes down to one of the rules for exceptions: they are for _exceptional_ situations, not for control flow. 

I don't know what your code does or how real time or critical it is, so take this as its face value: in most cases, exceptions are not a performance problem.

---

### Post by slavik on 2008-08-28
> **pmasiar said:**
> Of course.

It depends if I wear my CompSci hat, or my SolveItYesterday hat :-) When in hurry, I don't want to think how GC could be implemented, i want to have it and not to worry abut it.

> Remember the discussion about string concatenation? ... You should know one level under what you are working at, that is the only way you can be efficient at whatever level you are working at. Would you disagree with that?

That would be optimal, but not always possible. We are far from perfect.

-------

I was thinking not about how to implement exceptions (I remember first time reading about them - what a brilliant idea I thought, instead of GOTO). I was thinking about how language shapes our thinking about ways to solve a problem, and how non-obvious is it to overcome that influence.
right, but in this case, I was not concerned about USING an exception.

I guess it's a hobby of mine, take some feature from a higher level language (exceptions, garbage collection, OO) and see how it could be implemented in a lower level language (like C).

EDIT: Please remember that this thread is not a discussion on whether exceptions are good/bad or anything of the sort, this is more of a "how to create exceptions in a language that doesn't have them built in."

---

### Post by cb951303 on 2008-08-28
[http://www.nicemice.net/cexcept/](http://www.nicemice.net/cexcept/)

Exceptions in C with the regular try catch block. its just a simple macro that wraps longjmp() and setjmp() to implement a nice exception handling system.

---

### Post by slavik on 2008-08-28
> **cb951303 said:**
> [http://www.nicemice.net/cexcept/](http://www.nicemice.net/cexcept/)

Exceptions in C with the regular try catch block. its just a simple macro that wraps longjmp() and setjmp() to implement a nice exception handling system.
nice find! :D ... even better than what I thought of ... :)

---

### Post by cb951303 on 2008-09-03
> **slavik said:**
> nice find! :D ... even better than what I thought of ... :)

yeah I use it all the time, very simple and effective solution

---

