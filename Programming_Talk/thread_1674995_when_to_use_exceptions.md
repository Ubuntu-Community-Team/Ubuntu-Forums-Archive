---
title: "when to use exceptions?"
date: 2011-01-24
forum: Programming Talk
---

### Post by worksofcraft on 2011-01-24
I got in the habit of rarely using exceptions because they weren't around when I learnt C++.

Today I'm working on extending AGG graphics library with input methods for popular graphics formats and wondering if anyone has any views on what role exceptions should play in this kind of general purpose scenario.

For instance:

I make general purpose get_jpeg_image(aFileName) method but say it is called to read a file that is wrong format (like it could be png)...

Would it be a better design for my function to return with an error status, or to throw an exception?
The first could be used in an if statement so one can then try a different format, while the other can be caught if one has other formats to try.

Another example:

Say I read an image and it has the wrong dimensions and doesn't fill my designated image rectangle in my image buiffer, or perhaps it is too big...
Would it be better to throw an exception, or just to carry on and do something arbitrary? (Like center and clip the image to that area)

Any thoughts welcome :)

---

### Post by Reiger on 2011-01-24
I a high level language this would be easy: throw exceptions. But you're doing C++ so you need to consider whether or not the general design of the library facilitates client code without memory leaks, or whether it becomes too painful to contemplate.

---

### Post by worksofcraft on 2011-01-24
> **Reiger said:**
> I a high level language this would be easy: throw exceptions. But you're doing C++ so you need to consider whether or not the general design of the library facilitates client code without memory leaks, or whether it becomes too painful to contemplate.

Very good point.

I'm using a simple C library named libjpeg (and another is libpng) to do the actual compression and decompression.

By default, libjpeg adopts setjmp/longjmp for error handling... which is what made me consider exceptions in the first place, because of course setjmp/longjump won't even unwind the destructors for things on the stack frame, let alone tidy up dynamic memory allocations :shock:

Thus I think you convinced me already that I be better off catching the setjmp/longjmp malarkey and tidying up the libjpeg structures before returning an error code.

I'm still not sure about when image dimensions don't fit.
Ultimately one would want a set of different options like tile the image to fill the designated space, center the image, resize the image etc... and all of those except for clip will require a complete image and a separate function to adapt and transfer it in the desired way.

Thus at base level I will do two routines:
[LIST=1]
[*] creates a memory resident image from file so that it exactly  matches the dimensions in the file and can then be transferred in whatever way one wants to another image.

[*] efficiently decompresses image directly to designated area clipping excess and leaving unused space unchanged.
[/LIST]

I'll be interested in other views too because I really do think one gets a much better design bouncing ideas of other people in forums like this one :)

---

### Post by nvteighen on 2011-01-25
I hate exceptions, except for very specific cases.

My main reason is that they introduce another interfacing factor which is actually unpredictable, therefore forcing you to always check for exceptions... Also, I don't like the fact that they are passed through call stacks and only signal an error if uncaught in at the topmost frame. In some cases, that behaivor makes everything much more confusing (who's throwing that and who should catch it?).

I prefer using the return value as a *general* output interface for my functions/methods. In other words, if I need my function to send out some information, whether a data structure or an error code or whatever, I want this to be done through the same information channel. It can lead to some contrived code in a language without dynamic typing, like C or C++, but it makes everything clearer.

But, sometimes I use exceptions. Usually, as a last resort for extreme situations where just tell the function to return doesn't really work because it becomes a mess or because I want to encapsulate the context into some object or because I'm working with a library designed to use exceptions (even then I usually convert them to error codes)... In other words, I use exceptions exceptionally :P

---

### Post by worksofcraft on 2011-01-25
> **nvteighen said:**
> I hate exceptions, except for very specific cases.

My main reason is that they introduce another interfacing factor which is actually unpredictable, therefore forcing you to always check for exceptions... Also, I don't like the fact that they are passed through call stacks and only signal an error if uncaught in at the topmost frame. In some cases, that behaivor makes everything much more confusing (who's throwing that and who should catch it?).

I prefer using the return value as a *general* output interface for my functions/methods. In other words, if I need my function to send out some information, whether a data structure or an error code or whatever, I want this to be done through the same information channel. It can lead to some contrived code in a language without dynamic typing, like C or C++, but it makes everything clearer.

But, sometimes I use exceptions. Usually, as a last resort for extreme situations where just tell the function to return doesn't really work because it becomes a mess or because I want to encapsulate the context into some object or because I'm working with a library designed to use exceptions (even then I usually convert them to error codes)... In other words, I use exceptions exceptionally :P

Also good point. So like I'll use exceptions only for things that are genuinely "unrecoverable" errors.

For instance, in this case once I established that it IS a jpeg file but then say the file format turns out to be unreadable it will throw...

An application might exceptionally catch that to go back to a file selection menu offering the user a new choice, but it's not intended as a regular part of the algorithm in choosing which decoder to use.

---

### Post by slavik on 2011-01-25
> **nvteighen said:**
> I hate exceptions, except for very specific cases.

My main reason is that they introduce another interfacing factor which is actually unpredictable, therefore forcing you to always check for exceptions... Also, I don't like the fact that they are passed through call stacks and only signal an error if uncaught in at the topmost frame. In some cases, that behaivor makes everything much more confusing (who's throwing that and who should catch it?).

I prefer using the return value as a *general* output interface for my functions/methods. In other words, if I need my function to send out some information, whether a data structure or an error code or whatever, I want this to be done through the same information channel. It can lead to some contrived code in a language without dynamic typing, like C or C++, but it makes everything clearer.

But, sometimes I use exceptions. Usually, as a last resort for extreme situations where just tell the function to return doesn't really work because it becomes a mess or because I want to encapsulate the context into some object or because I'm working with a library designed to use exceptions (even then I usually convert them to error codes)... In other words, I use exceptions exceptionally :P
your main reason is because developers are lazy. I do application support and see stack traces all the time and the word from developers is that they are 'normal' ... I am pretty sure they do stupid things like:

```

return_type myfunc_in_myclass (some_type some_arg) {
// some code
try {
  // some code that might throw
} catch (Exception e) {
  System.printStackTrace();
}
// some more code
}

```

gee, my function throws exceptions sometimes, I wonder why ...

---

### Post by trent.josephsen on 2011-01-26
Like nvteighen, I hate exceptions and use them only when not doing so means mangling the code beyond all usefulness.

I try to avoid ever catching exceptions, choosing instead to make sure that the parameters are valid before calling a function that could throw something... probably evidence of my C habits leaking through.

I also try to avoid explicitly throwing exceptions, letting the library functions I use do the dirty work.

This is one of those things that I don't think I can explain without an example... okay, so say there's an "open" function that returns a file, and a "write" function that takes a file parameter.  open() should be able to handle insufficient permissions, file-not-found, etc., because those kinds of things can be detected within the open() call and are typical things that open() might have to deal with -- they aren't "exceptional circumstances".  Similarly, write() should be able to deal with disk-full and quota errors without throwing an exception; presumably, the calling code knows what to do when write() returns ERR_DISK_FULL (or whatever).

Where an exception might creep into this scenario is when client code carelessly passes the result of open() into write() without checking to see whether open() was successful or not.  In the case of an invalid file object, write() should throw an exception back to the careless client.

Generally, I suppose, you could say that a function only need throw an exception if it is used without setting up the environment or parameters correctly; problems it encounters while doing its own job should be returned as an error code.

factorial(-1) might be another example of an exception-throwing call.  Code that calls factorial() should be aware that the domain of the factorial function does not include -1, and should not try to call it with such obviously bogus input.

My $0.02

---

### Post by trent.josephsen on 2011-01-26
sorry, double post

---

### Post by worksofcraft on 2011-01-26
> **trent.josephsen said:**
> Like nvteighen, I hate exceptions and use them only when not doing so means mangling the code beyond all usefulness.

I try to avoid ever catching exceptions, choosing instead to make sure that the parameters are valid before calling a function that could throw something... probably evidence of my C habits leaking through.

I also try to avoid explicitly throwing exceptions, letting the library functions I use do the dirty work.

This is one of those things that I don't think I can explain without an example... okay, so say there's an "open" function that returns a file, and a "write" function that takes a file parameter.  open() should be able to handle insufficient permissions, file-not-found, etc., without throwing an exception, because those kinds of things can be detected within the open() call and are typical things that open() might have to deal with -- they aren't "exceptional circumstances".  Similarly, write() should be able to deal with disk-full and quota errors without throwing an exception; presumably, the client code knows what to do when write() returns ERR_DISK_FULL (or whatever).

Where an exception might creep into this scenario is when client code carelessly passes the result of open() into write() without checking to see whether open() was successful or not.  In the case of an invalid file object, write() should throw an exception back to the careless client.

Generally, I suppose, you could say that a function only need throw an exception if it is used without setting up the environment or parameters correctly; problems it encounters while doing its own job should be returned as an error code.

factorial(-1) might be another example of an exception-throwing call.  Code that calls factorial() should be aware that the domain of the factorial function does not include -1, and should not try to call it with such obviously bogus input.

My $0.02.  Don't know how good a job I've done of communicating though.

I would have thought that a "disk full" error would be quite exceptional and not the kind of status I would expect users of my library to test for and generate appropriate error messages, so I'm kind of just letting that sink in... You seem to be saying only use them to trap software bugs :confused:

I really do like your example of factorial(-1), because not that long ago I was having a discussion about a need to discriminated discrete numbers from continuous ones. (At the time someone programmed factorial in a language called Python and didn't realize there could be issues with not knowing what kind of number was going to be used!)

You see there is actually an [extended concept of factorial]("http://en.wikipedia.org/wiki/Factorial#Extension_of_factorial_to_non-integer_values_of_argument") and someone calling the function with a parameter of -1 might not be aware that the function they were calling wasn't actually ever coded to cope for his or her extended concept and so it might exhibit undefined behavior :shock:
 IOW I totally agree with throwing some kind of exception in that case ;)

---

### Post by trent.josephsen on 2011-01-26
> **worksofcraft said:**
> I would have thought that a "disk full" error would be quite exceptional and not the kind of status I would expect users of my library to test for and generate appropriate error messages, so I'm kind of just letting that sink in...

Maybe on a desktop system with 1+ TB of hard drive space.  What about an embedded system that logs mundane activity to some tiny storage device and deletes old stuff when it gets full?  Maybe your program runs as an unprivileged user with only 10MB of quota?  Different applications will have different ways to handle running out of space -- delete old files, empty cache, suspend and wait for something else to make space, continue without logging, etc.

As I see it, finding out that the disk is full is an "occupational hazard" for the write() function; it can only happen *during* a call to write(), it's something that won't happen *unless* write() is called, and the error can't (easily) be detected *without* calling write() -- detecting it there makes sense.

Validating its parameters is *not* a responsibility of write(); it should have been done *before* the call was made, in the code that knew what to do with incorrect parameters (e.g., try a different filename, or prompt for user input).  In other words, if you pass an invalid file to write() or -1 to factorial(), it's your own fault and write() or factorial() doesn't bear responsibility for dealing with it -- that's exceptional.

>  You seem to be saying only use them to trap software bugs :confused:
More or less, yeah.  This isn't the only way to use exceptions, nor the only way I use them -- they do occasionally come in handy for jumping to error-handling code in a function two or three levels up.  But in general I think exceptions are a crude hack and use them mostly to work around sloppy code that isn't yet ready to ship.

Seems I've read a style guide with a section on exceptions, somewhere... there are other philosophies.

N.B. Even the gamma function is undefined at negative integers...

---

### Post by slavik on 2011-01-26
> **trent.josephsen said:**
> Maybe on a desktop system with 1+ TB of hard drive space.  What about an embedded system that logs mundane activity to some tiny storage device and deletes old stuff when it gets full?  Maybe your program runs as an unprivileged user with only 10MB of quota?  Different applications will have different ways to handle running out of space -- delete old files, empty cache, suspend and wait for something else to make space, continue without logging, etc.

As I see it, finding out that the disk is full is an "occupational hazard" for the write() function; it can only happen *during* a call to write(), it's something that won't happen *unless* write() is called, and the error can't (easily) be detected *without* calling write() -- detecting it there makes sense.

Validating its parameters is *not* a responsibility of write(); it should have been done *before* the call was made, in the code that knew what to do with incorrect parameters (e.g., try a different filename, or prompt for user input).  In other words, if you pass an invalid file to write() or -1 to factorial(), it's your own fault and write() or factorial() doesn't bear responsibility for dealing with it -- that's exceptional.


More or less, yeah.  This isn't the only way to use exceptions, nor the only way I use them -- they do occasionally come in handy for jumping to error-handling code in a function two or three levels up.  But in general I think exceptions are a crude hack and use them mostly to work around sloppy code that isn't yet ready to ship.

Seems I've read a style guide with a section on exceptions, somewhere... there are other philosophies.

N.B. Even the gamma function is undefined at negative integers...
I don't understand your argument. on one hand you say that exceptions are needed, on the other that they are a hack. I think you are confusing good code (properly caught exceptions) and bad code (where each function is just a giant try block).

exceptions are the error handling blocks of Java, period. although, there are some copies of classes that return null on error.

---

### Post by trent.josephsen on 2011-01-26
I never said exceptions were needed.

---

### Post by worksofcraft on 2011-01-27
> **trent.josephsen said:**
> 
As I see it, finding out that the disk is full is an "occupational hazard" for the write() function; it can only happen *during* a call to write(), it's something that won't happen *unless* write() is called, and the error can't (easily) be detected *without* calling write() -- detecting it there makes sense.

I see what you say... otoh what I'm strugling with is writing out an image file line by line somewhere nested in various calls to clipping and compressing the data. In such an application passing back and testing for "disk full" error seems just plain inconvenient since at no point is there a sensible way to deal with it other than aborting the output.

> **trent.josephsen said:**
> 
Validating its parameters is *not* a responsibility of write();

Validating that a file exists and has the correct permissions before passing it to a read function is also inconvenient.

What I've decided to do is made a reader object with constructor that takes the file name as parameter.
It saves the opened file handle in a member data field. Then the  destructor closes the file.
Constructors can't return a status value, so if the file open fails I throw an exception. Implicitly the destructor then won't get called to close a file that wasn't opened.

> **trent.josephsen said:**
> 
Seems I've read a style guide with a section on exceptions, somewhere... there are other philosophies.

> **slavik said:**
> 
exceptions are the error handling blocks of Java, period. although, there are some copies of classes that return null on error.



I'm quite interested in understanding why exceptions should be so much more accepted in other languages like Java... any chance you could post the link if you find it again?

---

### Post by SledgeHammer_999 on 2011-01-27
Well according to a pcsx2(playstation emulator) developer, C++ exceptions, in his specific use, are actually faster than error code checking and the try/catch code appears simpler than the equivalent error-checking code.

forum post->[http://forums.pcsx2.net/Thread-blog-C-exceptions-can-be-an-optimization](http://forums.pcsx2.net/Thread-blog-C-exceptions-can-be-an-optimization)

---

### Post by worksofcraft on 2011-01-27
> **SledgeHammer_999 said:**
> Well according to a pcsx2(playstation emulator) developer, C++ exceptions, in his specific use, are actually faster than error code checking and the try/catch code appears simpler than the equivalent error-checking code.

forum post->[http://forums.pcsx2.net/Thread-blog-C-exceptions-can-be-an-optimization](http://forums.pcsx2.net/Thread-blog-C-exceptions-can-be-an-optimization)

Hey... thanks for that link :)
It is an excellent discussion and in particular I think Jake's Edit is very applicable:
> Edit: I should add that the basic theory of optimization I'm using here is what I call "optimizing for the common case." It's a process of speeding up the code that's being run more frequently (which in our example above is a typically error-free running loop) by offloading the logic to an area of the code that's run much less frequently (the exception handler's entry/exit overhead). It's one of the most powerful optimization techniques any programmer can employ.

Writing out a transformed and compressed image line by line has many iterations of nested calls and moving error handling out of the loop does seem like the right way to do it :guitar:

---

### Post by Reiger on 2011-01-27
> **worksofcraft said:**
> I'm quite interested in understanding why exceptions should be so much more accepted in other languages like Java... any chance you could post the link if you find it again?

Well in Java you have a garbage collector and with a little finally {} you can secure the OS resources (like file handles) as well. Finally is a good idea either way. So the trade off is between code silently doing the wrong thing (not checking error codes) or breaking down when as a result of a bug (not catching exceptions). 

Additionally, exceptions fit the class based programming model of Java quite nicely. Working with Exceptions is like working with any other object type should you need to inspect them. No re-interpretation of values necessary (although enums go some way towards hiding that problem).

---

### Post by worksofcraft on 2011-01-27
> **Reiger said:**
> Well in Java you have a garbage collector and with a little finally {} you can secure the OS resources (like file handles) as well. Finally is a good idea either way. So the trade off is between code silently doing the wrong thing (not checking error codes) or breaking down when as a result of a bug (not catching exceptions). 

Additionally, exceptions fit the class based programming model of Java quite nicely. Working with Exceptions is like working with any other object type should you need to inspect them. No re-interpretation of values necessary (although enums go some way towards hiding that problem).

Hum... well I never did find a full featured garbage collector for C++ but TBH I think it is overrated:

Dynamically allocated objects in C++ I tend to put in containers, or reference from other objects that take care of their disposal on destruction and that have precisely defined scope.

I tend to just think that throwing an exception is like an alternative kind of **return statement**. It returns to an earlier context rather than the immediate caller with type of result appropriate to the target context.

It does dispatch all stack frame destructors on the way so I don't expect too many problems :)

---

### Post by nvteighen on 2011-01-28
I've been thinking about this lately. Specially because in PycTacToe I've had a situation where I had to choose whether to use an exception-based error checking or one based on an return value. I first used an exception, but ended up changing it to a return value.

I've already stated my point about exceptions: that they add another interfacing element. I forgot to point this out in my previous post, but in my opinion, the fact that the "correct" signature of an exception-throwing C++ function is:

```

int whatever(std::vector<char>& something) throw(some_exception);

```

is very representative of what I don't like of exceptions. Ok, I'm aware that that particular signature syntax is particular to C++, but the semantics of it are present in Java or Python. The exceptions a function can throw constitute part of the function's interface.

That said, my experience is that exceptions are better used for very specific situations like the ones trent.josephsen points out: e.g. where you use an exception as a "soft" interrupt that allows for proper shutdown of your program. That's something that a return value may not handle correctly because you may need information from the function's call stack in order to reconstruct the context to perform the cleaning. That's why exceptions are classes: because they usually allow you to pass some data to its constructor so the catching block can inspect that data and do something according to it.

But I really don't like adding complexity to my interfaces when not needed. In other words, I think it's completely wrong to use exceptions just to return from a function without using them to encapsulate part of the faulty context that originated the error. That can be done by using a simple return value. And if you're concerned by expresiveness, you could use an enum type or a macro (or a const global variable).

Maybe is it just me?

---

### Post by ziekfiguur on 2011-01-28
The general rule i use is: "Return values are better than exceptions, but exceptions are better than jumps".

Also, for C++ (I know they do thing differently in Java) i think exceptions should, as their name suggest, be exceptional.

---

### Post by trent.josephsen on 2011-01-28
> **nvteighen said:**
> in my opinion, the fact that the "correct" signature of an exception-throwing C++ function is:

```

int whatever(std::vector<char>& something) throw(some_exception);

```

is very representative of what I don't like of exceptions.

This.  I might get more use out of exceptions if adding one little "throw whatever" in the bottom of the call stack didn't require me to change the declarations and documentation of all the functions that enclose it.  This was one of the strangest things to me about Java (and why I prefer Python's strategy).

---

