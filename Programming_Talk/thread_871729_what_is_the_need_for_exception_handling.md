---
title: "what is the need for exception handling?"
date: 2008-07-27
forum: Programming Talk
---

### Post by sharks on 2008-07-27
what is the need for exception handling?
    suppose we need to give exception for dividing by 0,we can use IF statement to make sure the value is not zero.
    Does it give any special advantage?

---

### Post by scragar on 2008-07-27
what language? in a fair number of languages that should throw an error, so I like to use error handleing, although your needs may make alternate requirements for such things.

---

### Post by NovaAesa on 2008-07-27
Okay, so with dividing by zero you could check before hand. But you can't always check before hand if something is going to throw an error. For example, say you are going to try to write to a file. What happens if you don't have write access to the file or if it doesn't exist?

Error handling for things like div by zero would be a pain in the butt and useless most of the time, but for most other things error handling is a godsend.

---

### Post by scragar on 2008-07-27
> **NovaAesa said:**
> Okay, so with dividing by zero you could check before hand. But you can't always check before hand if something is going to throw an error. For example, say you are going to try to write to a file. What happens if you don't have write access to the file or if it doesn't exist?

Error handling for things like div by zero would be a pain in the butt and useless most of the time, but for most other things error handling is a godsend.

I dunno, a good error handling script can avoid the need to check perms before trying to write to a file or whatever, and since the error handling script can be reused with only a few minor edits it can be considerably more efficient in the time spent programming to simply include an error handler and just code ignoring the chance of such errors.

---

### Post by dribeas on 2008-07-27
> **sharks said:**
> what is the need for exception handling?
    suppose we need to give exception for dividing by 0,we can use IF statement to make sure the value is not zero.
    Does it give any special advantage?

You really should google for exceptions in your language, I am sure you can find some interesting articles about why you should use them.

There are a some reasons, as legibility of user's code, or that in some languages you cannot report errors in specific places in any other way.

Legibility

Error reporting can be done in different ways. Now assume that you have to implement a method that performs some calculation on two integers and returns a third integer, following your example, and that one of the steps includes a division. Now the question is what to do and how to do it. Without exceptions you have to add another data element to encode the errors, so you need to change the interface:

```

// No exceptions, C syntax
int calculate( int a, int b, int* result ); // Option 1
int calculate( int a, int b, int* ok ); // Option 2

```

And then user's algorithm will be tangled with error checking code:

```

// Assuming option 1: return value encodes success (COM style)
int a = 10, b = 20, c = 30, d, result, error_code;

error_code = calculate( a, b, &result ); // C syntax
if ( error_code == N_OK ) {
   // do whatever seems right when the operation has failed
}
error_code = calculate( result, c, &result );
if ( error_code == N_OK ) {
   // do whatever seems right when the operation has failed
}
// ... more code probably with the same format

```

With exceptions:

```

int calculate( int a, int b ); // C++ style, no explicit exception definition
int calculate( int a, int b ) throws (InvalidParameter); // Java style

// user code:
int a = 10, b = 20, c = 30, d, result, error_code;
try
{
   result = calculate( a, b );
   result = calculate( result, c );
}
catch ( InvalidParameter const & ) // C++ style catch
{
   // do error reporting, or whatever seems suitable
}

```

The algorithm is easier to read: it performs two calculations on the input numbers. Also the interface is cleaner, it just focuses on data inside and outside of the function (don't need to check what data elements are error reporting versus real data).

When you cannot use return codes

Constructors don't have a return value, you cannot use that for error reporting. Some people have suggested adding internal error attribute to  classes and then a post-construction check:

```

class X // C++ syntax
{
   X(); // Does not throw
   bool ok(); // Check whether the object was correctly constructed
//... 
};
// user code
{
   X *x = new X();
   if ( !x.ok() ) {
      delete x;
   }
   // use x
}

```

Again, user code has to mix the algorithm with error checking routines so that later on x is not used if it was not 'properly' constructed. Moreover, if construction has failed, then x was not 'constructed' it should not exists!

Code safety

Languages with exception support have special features to ensure that proper cleanup of acquired resources is performed. If your method acquires some resource (let's say it acquires a mutex, opens a DB connection, requests memory...) then you must ensure that those resources are freed at the proper time. If inside the calculate example above memory is requested and assuming that all that can be done when the invalid division is reached is returning without further processing, then your code must ensure that memory is freed before all and every return statement.

Some languages as Java have special finally blocks:
[CODE]
try
{
   // acquire resources and do processing
}
catch ( Exception e ) {
   // perform error reporting or whatever seems appropiate
}
finally {
   // release resources: connections, mutexes
}
[/COOE]

Language warrants that all exits paths will execute 'finally' code, so resources will always be freed.

Others

Now, there are specifics on exceptions and how to work with them for each language that supports them, together with some rationale about why exception declaration should/should not be explicit (this is kind of a never ending discussion). Read a good book or google for articles on exceptions and your language.

---

### Post by dribeas on 2008-07-27
> **scragar said:**
> I dunno, a good error handling script can avoid the need to check perms before trying to write to a file or whatever, and since the error handling script can be reused with only a few minor edits it can be considerably more efficient in the time spent programming to simply include an error handler and just code ignoring the chance of such errors.

I guess that the point NovaAesa was trying to make is that you cannot always check before hand. You can check whether you have persmission to open a file, but it is quite harder to check whether you can actually write: is there enough space in the drive for your file, will the network connection fail while writting into a shared drive? There are just so many things that can go wrong, and so many of them that are so unlikely that you don't want to intermix your code with error handling...

   David

---

### Post by Reiger on 2008-07-27
Exception handling is a very nifty thing, actually. For instance the idea of a generic exception handling script still works; but it will require much less code. For instance if your app should return exit codes you can much more easily assign each type of exception a code rather than using if's until you're fingers are stuck to the I & F keys.

Like this (Java) example
```

try 
{
/* Do something prone to exceptions here ... */
} catch (ExceptionType e) {

ExceptionHandlerObject ehbo= new ExceptionHandlerObject(e);
ehbo.doSomethingUseful();
System.exit(ehbo.code);
}

```

Now the ehbo object may have the following method:
```

public void doSomethingUseful() {
  switch (code) {
    case 1 : System.out.println("An IO error occured; code: "+code); break;
    case 2 : System.out.println("An Division error occured; code: "+code); break;
    default: System.out.println("Some error occured; code: "+code); break;
  }
}

```

---

### Post by dribeas on 2008-07-27
Good point, that is a nifty feature of exceptions, you can not only centralize all error checking code at one place inside the same method, but you can even centralize different methods exception processing into a single place.

> **Reiger said:**
> 
```

public void doSomethingUseful() {
  switch (code) {
    case 1 : System.out.println("An IO error occured; code: "+code); break;
    case 2 : System.out.println("An Division error occured; code: "+code); break;
    default: System.out.println("Some error occured; code: "+code); break;
  }
}

```

I would change it into:
```

public void processException( Exception e )
{
   try
   {
      throw e;
   }
   catch ( NullPointerException )
   {
      System.out.println( "Null pointer operation." );
      e.printStackTrace();
   }
   catch ( AnotherException )
   {
      // ... 
   }
}
```

Instead of a switch with codes as exception type has information on what the problem is. Converting to a code so that you can do a switch does not seem right.

The same can be done with C++ (slightly different though):
```

void f() {
   try 
   {
   } catch ( ... ) {
      handle_exception();
   }
}
void handle_exception()
{
   try 
   {
      throw;
   } 
   catch ( exception1 const & e )
   {
      // do something appropiate to this exception
   }
   catch ( exception2 const & e )
   {
      // ...
   }
}

```

I have some C++ CORBA wrapper that does precisely that. For all remote operations it caches all exceptions and calls a single error handling method that logs the error and takes proper action (requesting another remote object reference from the same or other server...) depending on what exception is caught. That error recovery takes about 50 lines that would have had to be replicated for each and every remote call.

   David

---

### Post by slavik on 2008-07-27
an exception is really an interrupt.

exceptions are a way to send error codes back without using the return value or making up some other weird scheme (like having return value address as part of the argument list).

IMO, diving anything by zero should be Inf. :)

---

### Post by scragar on 2008-07-27
> **slavik said:**
> 
IMO, diving anything by zero should be Inf. :)

still doesn't change the fact that most languages throw an error first and ofcourse not all languages support infinity as they should, nothing you can do about that then.

---

### Post by slavik on 2008-07-27
> **scragar said:**
> still doesn't change the fact that most languages throw an error first and ofcourse not all languages support infinity as they should, nothing you can do about that then.
and that's sad :(

---

### Post by Alasdair on 2008-07-27
Dividing anything by zero is undefined in mathematics as well as in programming, you just can't do it.

Consider the following:

If 3 divided by 0 is infinity, then 0 times infinity is 3. Also, if 2 divided by 0 is infinity, then 0 times infinity is 2. Since 0 x infinity must equal 0 x infinity, 2 must equal 3 - You can't treat infinity as a number.

---

### Post by slavik on 2008-07-27
as resistance in a wire goes to 0ohm, the current you can generate in that wire goes to infinity (super conductors have resistance of 0 and you can have any current through them at any voltage). :)

---

### Post by Alasdair on 2008-07-27
That's interesting, but it's also completely irrelevant.:) Computer programs are equivalent to mathematical proofs (the Curry-Howard isomorphism). Since allowing division by zero allows you to come up with any absurd proof any programs that utilized division by zero would likely return similarly absurd results; even if your compiler somehow allowed it.

---

### Post by LaRoza on 2008-07-27
> **slavik said:**
> as resistance in a wire goes to 0ohm, the current you can generate in that wire goes to infinity (super conductors have resistance of 0 and you can have any current through them at any voltage). :)

> **Alasdair said:**
> That's interesting, but it's also completely irrelevant.:) Computer programs are equivalent to mathematical proofs (the Curry-Howard isomorphism). Since allowing division by zero allows you to come up with any absurd proof any programs that utilized division by zero would likely return similarly absurd results; even if your compiler somehow allowed it.

What if a program is monitoring such things? Computer programs are not the same as mathematical proofs, and are used to solve real life problems.

---

### Post by Alasdair on 2008-07-28
I don't know whether it would be correct to say that proofs are equal to programs, but they are equivalent. The following program in a fictional 'InfiniteHaskell' language shows that the problem I pointed out previously applies to programming languages too.
```
absurdFunction :: Num a => a -> a -> a
absurdFunction x y = (x / y) * y
```
What does the function return? If x / 0 = infinity it can return any number for any input. Obviously in a purely functional language like InfiniteHaskell such a function cannot exist (it breaks referential transparency). Dividing by zero cannot be done in code for exactly the same reason as it can't be done in maths. The only sane thing to do is throw an error.

---

### Post by ceclauson on 2008-07-28
Exceptions are sometimes useful for detecting when a program isn't operating the way it should.  For instance, say you're trying to get the color of a pixel in an image, but the coordinates of the pixel are out of bounds due to a programming error.  If this didn't throw an exception, your program might proceed silently with bad data, and it would be difficult to detect the bug.  With an exception, you can pinpoint exactly where the program went wrong.

With regards to division by zero, Java actually supports this in floating point operations, and it evaluates to infinity or negative infinity depending on the sign of the numerator.  I believe JavaScript has the same feature.

---

### Post by nvteighen on 2008-07-28
> **slavik said:**
> as resistance in a wire goes to 0ohm, the current you can generate in that wire goes to infinity (super conductors have resistance of 0 and you can have any current through them at any voltage). :)

lim_x->0(a / x) = Inf. The result **goes** to infinity, it never really reaches it. Superconductors do have resistance, but that small that it can be considered to be near zero.

> **ceclauson said:**
> 
With regards to division by zero, Java actually supports this in floating point operations, and it evaluates to infinity or negative infinity depending on the sign of the numerator.  I believe JavaScript has the same feature.

Javascript returns NaN, if I remember well.

---

### Post by samjh on 2008-07-28
> **slavik said:**
> as resistance in a wire goes to 0ohm, the current you can generate in that wire goes to infinity (super conductors have resistance of 0 and you can have any current through them at any voltage). :)Current **goes to** infity != current **is** infinity.

In a superconductor, the persistence of the current is indefinite, not infinite.  And the current itself is not infinite: realistically it has a limit.

[quote=LaRoza]What if a program is monitoring such things? Computer programs are not the same as mathematical proofs, and are used to solve real life problems.[/quote]Studies in superconductivity require a solid grounding mathematical proofs, as it deals with values and changes of values that cannot be defined numerically.

Formulating mathematical proofs is an important skill in some areas of computer science, especially in software specification and verification, as formal specifications and verification methods used by the software engineering industry depend on mathematically proving that a software design cannot fail (ideally).

---

### Post by Lster on 2008-07-28
Division by zero is meaningless in any abstract sense (but perhaps not in the real world). As computers work abstractly, without the knowledge of what is "actually going on", I think the abstract model is most appropriate.

A good example is doing line intersections. If the two lines have an identical gradient, you will effectively divide by 0 while trying to find the coordinate of intersections. The coordinate is undefined!

Consider further that &#8734; cannot be manipulated by algebra without inconsistencies (as Alasdair demonstrated), and I think there's a strong argument for raising an error! :)

---

### Post by Lster on 2008-07-28
[QUOTE=nvteighen]Javascript returns NaN, if I remember well.[/QUOTE]

Actually, it doesn't seem to! ;)

---

### Post by lisati on 2008-07-28
There are merits in a catch-all style of dealing with errors, such as those already mentioned. The chief advantage is neater code. 

On the other hand, there are occasions where error avoidance is better, e.g. screening out "suspect" data in a collection of survey responses or experimental results.

---

### Post by samjh on 2008-07-28
> **lisati said:**
> There are merits in a catch-all style of dealing with errors, such as those already mentioned. The chief advantage is neater code. 

On the other hand, there are occasions where error avoidance is better, e.g. screening out "suspect" data in a collection of survey responses or experimental results.

Or you can use both:

- Screen out the suspect data and use exceptions to weed out the stragglers.

or 

- Screen out and deal with suspect data using exceptions in the screening code.

Overkill?  Sometimes, but often it is wise.

---

### Post by LaRoza on 2008-07-28
> **samjh said:**
> 
Studies in superconductivity require a solid grounding mathematical proofs, as it deals with values and changes of values that cannot be defined numerically.

Formulating mathematical proofs is an important skill in some areas of computer science, especially in software specification and verification, as formal specifications and verification methods used by the software engineering industry depend on mathematically proving that a software design cannot fail (ideally).

Mathematical proofs don't throw exceptions ;)

---

### Post by dribeas on 2008-07-28
> **Lster said:**
> Actually, it doesn't seem to! ;)

Ok, here and for all. What you can and cannot do with numbers is hardware defined. Languages can map operations on their abstract types to different hardware types (int/double...) but the processor is the one doing the work.

Integers do not allow division by 0. Floating point numbers (AFAIK in all current architectures) are implemented with [IEEE 754]("http://en.wikipedia.org/wiki/IEEE_754") standard that allows for real numbers plus some non-numbers as positive/negative infinity and other not-a-number NaN (unable to know).

Operations on these values are perfectly defined and do make sense in math. If you have a NaN, then any operation with that and another number will yield NaN, regardless of the second value. The same with infinities, infinity + any number = infinity, regardless of the number, except if the number is -infinity (both infinities are represented) in which case it is NaN.

Anyway this is for a different thread than 'what is the need for exception handling'

   David

P.S. By the way, all programmers should read how floating point numbers are stored and what you can and cannot do with them.

---

### Post by pmasiar on 2008-07-28
> **slavik said:**
> an exception is really an interrupt.

[http://en.wikipedia.org/wiki/Exception_handling](http://en.wikipedia.org/wiki/Exception_handling) can be implemented different ways, software [http://en.wikipedia.org/wiki/Interrupt](http://en.wikipedia.org/wiki/Interrupt) is one of them.

Program is correct one way, but wrong many different ways. Whole point of exception is that it will happen if something went wrong, regardless if you thought about testing for that particular way to be wrong or not.

[http://en.wikipedia.org/wiki/Superconductivity](http://en.wikipedia.org/wiki/Superconductivity) - resistance is truly zero, but it is limited by other factors: temperature and IIRC magnetic field density? 

> exceptions are a way to send error codes back without using the return value or making up some other weird scheme (like having return value address as part of the argument list)

... in a language like Perl, with OOP and exception bolted-in as afterthought. :-) Modern languages like Python or Java can use exception to handle control flow in a more meaningful way, handling different types of exception differently and in a more natural way.

> IMO, diving anything by zero should be Inf. :)

How Inf will fit into 32 bites, or whatever your register size is? And can I do Inf+1? 

Whole point of exception is that result is completely different that non-exception value. Having special symbol for it work in theory but not in practice.

---

### Post by KingTermite on 2008-07-28
> **sharks said:**
> what is the need for exception handling?
    suppose we need to give exception for dividing by 0,we can use IF statement to make sure the value is not zero.
    Does it give any special advantage?

Yes, for a few different reasons (sorry if these are repeated, I didn't read entire thread).

1. Some statements have many, many possible things that ought to be checked for. Your code will begin to look very sloppy if you have 27 if statements to check for possible wrong doings.

2. Its often good to wrap an entire block of code and then just trap "any" exception. Often you know the exceptions are nothing you can fix, or you just want the same exit to happen regardless of error. Rather than having 27 checks x 8 lines that need them, you can just wrap the entire block in one try and do a catch for all possible exceptions thrown.

3. Lastly, you don't want to ignore exceptions....unless you want your code to be just like early windows applications that gave a GENERAL PROTECTION FAULT (or blue screen in later windows versions) all the time. That's essentially what many exceptions will give you.

---

### Post by dribeas on 2008-07-28
> **KingTermite said:**
> 3. Lastly, you don't want to ignore exceptions....unless you want your code to be just like early windows applications that gave a GENERAL PROTECTION FAULT (or blue screen in later windows versions) all the time. That's essentially what many exceptions will give you.

That is an interesting and complex in itself. (Opinion) Sometimes you want and sometimes you don't want to catch all exceptions. Exceptions should propagate up to the point where appropiate actions can be performed. 

If you implement a function in a library there will be some exceptions for which you can make decisions and some where you don't. In those cases exceptions must propagate to the caller.

A simple example would be a configuration parser class/library. If the file cannot be read/write you cannot silently ignore the IO operation exception, the user must know. And it is the user (code) that must decide what is apropiate: is reading the file a requirement, or is it just optional user overrides for defaults in your application? In some cases exceptions should propagate so that the user, having a wider view can make her own decision.

---

### Post by KingTermite on 2008-07-28
> **dribeas said:**
> That is an interesting and complex in itself. (Opinion) Sometimes you want and sometimes you don't want to catch all exceptions. Exceptions should propagate up to the point where appropiate actions can be performed. 

If you implement a function in a library there will be some exceptions for which you can make decisions and some where you don't. In those cases exceptions must propagate to the caller.

A simple example would be a configuration parser class/library. If the file cannot be read/write you cannot silently ignore the IO operation exception, the user must know. And it is the user (code) that must decide what is apropiate: is reading the file a requirement, or is it just optional user overrides for defaults in your application? In some cases exceptions should propagate so that the user, having a wider view can make her own decision.
That's why you can rethrow the exception to do something of your own and then repropigate it up if you so desire. They didn't arbitrarily decide to let user's throw exceptions...and its not "just" so users can create/throw their own exceptions either. :)

---

### Post by pmasiar on 2008-07-28
> **dribeas said:**
> Exceptions should propagate up to the point where appropiate actions can be performed.

Exactly. And exceptions propagate much better than if-then clauses in the code :-)

---

### Post by tinny on 2008-07-28
WOW, Mathematical proofs, Superconductivity, IEEE standards being referenced!

Another how can I make myself look smart thread on the good old Ubuntu programming forum.

Here is my 5 cents...

Have a look into the whole checked / unchecked exceptions argument of Java vs C#. This is quite a major difference between Java and C# and is a bit of a mind shift. (Take it from one of the few people around here that has actually used both of these languages beyond "Hello World").

"Check" this out
[http://www.psynixis.com/blog/2007/06/06/the-ungreat-checkedunchecked-exceptions-debate/](http://www.psynixis.com/blog/2007/06/06/the-ungreat-checkedunchecked-exceptions-debate/)

Summary: Yes each approach is different, both do the job fine! 

Just write code and stop talking about it people!!!

---

### Post by slavik on 2008-07-28
> **tinny said:**
> WOW, Mathematical proofs, Superconductivity, IEEE standards being referenced!

Another how can I make myself look smart thread on the good old Ubuntu programming forum.

Here is my 5 cents...

Have a look into the whole checked / unchecked exceptions argument of Java vs C#. This is quite a major difference between Java and C# and is a bit of a mind shift. (Take it from one of the few people around here that has actually used both of these languages beyond "Hello World").

"Check" this out
[http://www.psynixis.com/blog/2007/06/06/the-ungreat-checkedunchecked-exceptions-debate/](http://www.psynixis.com/blog/2007/06/06/the-ungreat-checkedunchecked-exceptions-debate/)

Summary: Yes each approach is different, both do the job fine! 

Just write code and stop talking about it people!!!
woah!!! exceptions have an extra word in the front ... too long for me :P (I am not really fond of exceptions tbh).

I also disagree with not being able to propogate error-checking up ...

if (!somefunc()) { return; } and such :)

---

### Post by tinny on 2008-07-28
> **slavik said:**
> woah!!! exceptions have an extra word in the front ... too long for me :P (I am not really fond of exceptions tbh).

I also disagree with not being able to propogate error-checking up ...

if (!somefunc()) { return; } and such :)

Yeah one extra word... that's why I really dont care :)

I find both work, but I do have a little preference for checked exceptions (only just though).

I find in practice (writing applications with 100,000+ lines of code) that I never seem to have to catch more than say 5 exceptions max. If your catching a ton of exceptions then your design probably sucks (A language independent topic and completely removed from the check / Uncheck exceptions argument).

---

### Post by slavik on 2008-07-28
> **tinny said:**
> Yeah one extra word... that's why I really dont care :)

I find both work, but I do have a little preference for checked exceptions (only just though).

I find in practice (writing applications with 100,000+ lines of code) that I never seem to have to catch more than say 5 exceptions max. If your catching a ton of exceptions then your design probably sucks (A language independent topic and completely removed from the check / Uncheck exceptions argument).
I'm more of the mindset "you sign your life away when you invoke the compiler" (iow: "nobody will babysit you") :)

---

### Post by pmasiar on 2008-07-29
> **slavik said:**
> (I am not really fond of exceptions tbh).

I also disagree with not being able to propogate error-checking up ...

What is your preferred method to deal with unexpected situation? Check for them? :-)

---

### Post by nvteighen on 2008-07-29
> **pmasiar said:**
> What is your preferred method to deal with unexpected situation? Check for them? :-)
Yes, because my preferred language (you know me, right?) doesn't support exceptions... or sending return-codes across several functions calls... It's an interesting way to get insane.

---

### Post by LaRoza on 2008-07-29
> **pmasiar said:**
> What is your preferred method to deal with unexpected situation? Check for them? :-)

That is mine. My system restore program is functional, but I have to redo the code to use exceptions. No way I am going to release my fortran-python code...

---

### Post by pmasiar on 2008-07-29
> **nvteighen said:**
> Yes, because my preferred language (you know me, right?) doesn't support exceptions... or sending return-codes across several functions calls... It's an interesting way to get insane.

Obviously, if your language does not support exception, it's hard to use them :-)

But exceptions were introduced to help keep sanity during error handling (then screwed up in Java by requiring **static** checking of exceptions, exactly the wrong thing to do).

But I am really interested in slavik's opinion, because he is such vocal proponent of superiority of Perl (which is dynamically typed, but has kinda exceptions kludge bolted on), and also I have hard time to understand "I also disagree with not being able to propogate error-checking up ..." - I counted two negations...

> I'm more of the mindset "you sign your life away when you invoke the compiler" (iow: "nobody will babysit you")

"sign your life away" compared to what? (when using non-compiled language)

From this comment, it looks like slavik prefers runtime exception over type checking - but dynamic type checking is just one (simple) kind of exception. And many people confuse dynamic typing with strong typing: Perl is weakly dynamically typed, Python is strongly dynamically typed. Is it sign of blubishness?

---

### Post by Sinkingships7 on 2008-07-29
> **LaRoza said:**
> That is mine. My system restore program is functional, but I have to redo the code to use exceptions. No way I am going to release my fortran-python code...

I still can't wait for that. I remember you introducing it as a "prototyped" idea, if you will, a few months ago. Glad to hear you've got it to be functional.  :)

---

### Post by LaRoza on 2008-07-29
> **Sinkingships7 said:**
> I still can't wait for that. I remember you introducing it as a "prototyped" idea, if you will, a few months ago. Glad to hear you've got it to be functional.  :)

I wasn't going to release it, but I actually used it myself, so it at least works the way I wanted it to.

I have to read up on exceptions though to redo that part.

---

### Post by nvteighen on 2008-07-29
> **pmasiar said:**
> 
But exceptions were introduced to help keep sanity during error handling (then screwed up in Java by requiring **static** checking of exceptions, exactly the wrong thing to do).

I know, I have used exceptions in Javascript and really miss them ;) As I'll soon go for Python (as soon as I end my ncurses experiment in C), and have got interested on that exceptions as classes treatment. It really sounds an interesting feature to keep an eye at...

---

### Post by Sinkingships7 on 2008-07-29
> **LaRoza said:**
> I wasn't going to release it, but I actually used it myself, so it at least works the way I wanted it to.

I have to read up on exceptions though to redo that part.

I hope you release it. That seems to be a much-requested feature which Ubuntu (Linux?) lacks.

---

