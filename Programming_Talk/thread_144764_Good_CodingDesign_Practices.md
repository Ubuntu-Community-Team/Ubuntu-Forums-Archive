---
title: "Good Coding/Design Practices"
date: 2006-03-15
forum: Programming Talk
---

### Post by krypto_wizard on 2006-03-15
I hate to discuss code but I am struggling badly with my design of code which is inculcating bad progrmaming habbits in me.

I still wonder how to write nice clean code. I am good at implementing logic but bad at programming management skills. I have not written code for big projects in my life. Writing couple of classes is ok for me but as code size grows I suck.

Also, one of my inabilities is to debug the code. I wrote lot of code and when I thought its done did I start to run(execute) the program, which I think isn't good programming practice.

Every help is appreciated to think as a software engineer, define and design classes and manage and debug the code systematically.

Thanks, Every help is appreciate.

---

### Post by gord on 2006-03-15
i can't claim to be an expert on this, but in my years iv figured out at least a few things;
[LIST]
[*]indent - for the love of god, indent.
[*] be consistant - figure out a style of coding and stick with it, when you come back to that code in 6 months time, you'll be very greatfull 
[*]document the crap out of it - but remeber, quality over quantity.
[*]structure your code - don't just bung everything in a directory called src ;)
[*]give variables real names - don't call something 'i' or 'v' or whatever, make sure they have good names so that you'll know what they do without reading the rest of your code. for example, instead of using 'i' for a counter, use 'ctr'.
[/LIST]

course, these are just things that i try to adhere to, everyones got a diffirent opinion im sure ;)

---

### Post by krypto_wizard on 2006-03-15
How about some design and code debugging tips ?

> **gord]i can't claim to be an expert on this, but in my years iv figured out at least a few things said:**
> 
[*]indent - for the love of god, indent.
[*] be consistant - figure out a style of coding and stick with it, when you come back to that code in 6 months time, you'll be very greatfull 
[*]document the crap out of it - but remeber, quality over quantity.
[*]structure your code - don't just bung everything in a directory called src ;)
[*]give variables real names - don't call something 'i' or 'v' or whatever, make sure they have good names so that you'll know what they do without reading the rest of your code. for example, instead of using 'i' for a counter, use 'ctr'.
[/LIST]

course, these are just things that i try to adhere to, everyones got a diffirent opinion im sure ;)

---

### Post by psychicdragon on 2006-03-15
Here are a couple pointers on project design:

Before you even start coding you should visualize your program and take some notes. You should ask yourself:

What classes do you need to create?
What kind of objects do they represent? (file, database, window, whatever)
How do the different objects interact with each other?

Then, there are the stylistic issues that gord mentioned. Commenting code is very important, I'm often guilty of poorly documenting my code. It is really a pain in the *** when you have to update some code you wrote months ago that you failed to document properly.

Not putting tons of unrelated classes in one file is a good idea as well.

---

### Post by qux on 2006-03-15
> 
I still wonder how to write nice clean code. I am good at implementing logic but bad at programming management skills. I have not written code for big projects in my life. Writing couple of classes is ok for me but as code size grows I suck.


[http://ei.cs.vt.edu/~cs2604/Standards/Standards.html](http://ei.cs.vt.edu/~cs2604/Standards/Standards.html)

I really recommend you read this; I follow it to the letter and my code is much cleaner and easier to read and maintain because of it.

> 
Also, one of my inabilities is to debug the code. I wrote lot of code and when I thought its done did I start to run(execute) the program, which I think isn't good programming practice.


try doing the opposite. Implement little portions, test it thoroughly and then build on top of it piece by piece; this is what i do and it works to great effect.

If your not using a debugger, i really recommed you do. If you feel intimidated
by the command line there should be a GUI front end available. Debuggers have a learning curve but they really are invaluable tools to have at ones disposal.

Another form of debugging is using your languages output routines; this is effective for seeing what values are stored in variables, or testing to see if a block of code is being executed inside a loop or conditional statement or whatever. It messes up the code somewhat, but it's only temporary right?

---

### Post by jerome bettis on 2006-03-15
[http://www.psgd.org/paul/docs/cstyle/cstyle01.htm](http://www.psgd.org/paul/docs/cstyle/cstyle01.htm)

---

### Post by toojays on 2006-03-15
A couple of tips in addition to what others have said:

If you write C or C++, learn to use valgrind. Run your program under valgrind every now and then and tidy up and memory bugs it complains about.

The other one is that whenever you think you have finished writing a function, read it. What I mean by that is, try to image what another programmer would think if they read your code. Could they just read a single function, or would they need to jump all over the place to figure out what your code does? To be able to answer that question, you need to read other programs of varying quality.

Another rule of thumb is to try and make each function contain not much more than a screenful of code. Maintaining programs where there are many functions longer than 1000 lines just isn't fun.

---

### Post by sapo on 2006-03-15
I think that all coders should read this:

[http://thc.org/root/phun/unmaintain.html](http://thc.org/root/phun/unmaintain.html)

---

### Post by ow50 on 2006-03-15
For the debugging, I'd recommend writing some test code. I just recently added test code for a large application and I wish I had done it already when I started.

Based on your previous posts, you're using Python, right? Simplest test code could look like
```
def add(x, y):
    return x + y
    
if __name__ == '__main__':

    assert add( 0, 1) == 1
    assert add( 2, 2) == 4
    assert add(-1, 2) == 1
```

That way you can test individual modules first, when you write new code. Once that new code works based on the tests, run the whole app. You can also have some system to run all tests for all modules and you can run that once in a while to make sure some new code hasn't broken any existing code elsewhere.

There's some actual testing frameworks, e.g.
[unittest](http://docs.python.org/lib/module-unittest.html)
[py.test](http://codespeak.net/py/current/doc/test.html)
but if you don't like them, you can easily roll your own.

---

### Post by LordHunter317 on 2006-03-15
> **qux][http://ei.cs.vt.edu/~cs2604/Standards/Standards.html](http://ei.cs.vt.edu/~cs2604/Standards/Standards.html)

I really recommend you read this said:**
> Unfortunately, it's crap.

I'll explain why.  It's rules on documentation are totally incorrect: You shouldn't have to document "what" a function does in comments.  You should be striving to write code that's simple and concise enough that the what is obvious from reading the code.  What should be documented is "why" the function exists and does what it does: how it relates to the project requirements, how it was refactored to become common code.  "What" should only ever be documented when it's difficult to understand or not obvious.

BUG, XXX, TODO, etc. should always be *at the site* of the problem, never at the top of the file.  I have an IDE that searches for these things for a reason.

Subroutines really ought to be written not in single logical units, but in a single unit *that makes the most sense to a programmer*.  Then afterwards, they should be pared down as necessary for the following reasons:[list][*]Their length is an impedement to understanding[*]They duplicate common code that should be factored into another function[*]The behavior of the function is more distinct.[/list]This practice is no different from writing a draft and then editing before reaching the final paper.  The goal of the first draft is to get the words on the page, coding is frequently no different.  Obviously, the rules are different if you have a specification to follow.

Their rules about number of parameters are bunk.  Their rule about not passing by reference is not only bad to begin with, *it's totally inapplicable* in this day and age when your always passing by pointer in most languages.

Variables don't need comments unless their usage is non-obvious.

Same with block statements.  Whoever wrote this did no real-world coding.

He's wrong about goto and C.  SESE is prefectly valid error handling in C, and frequently more readable than the alternatives.  You can't break loops of arbitrary depth in C without lots of conditionals.

[quote=jerome bettis]http://www.psgd.org/paul/docs/cstyle/cstyle01.htmThe commentary there is valid for C and C only.  Much of it isn't even correct for C++ and would even be out and out wrong.

However, precious little of the help given was actual design help.  So, let's see:[list][*]Write your design down on paper first.  How you do it doesn't matter.  Requirements document.  UML.  Something.  You need to understand, in whatever language you think in, what you're doing.[*]Make sure whatever you wrote down matches what you actually want to code.[*]A common trap is assuming that classes must  a) completely model their real-world counterpart b) must model something in the real-world.  Both are false.  An object should model only whatever set of behaviors is useful to the program, and any set of useful behaviors is a valid candidate for being a class.  A perfect example is a class that represents an event or message sent between objects.[*]If you're not sure what you're supposed to code, write it down.[*]Factor out common functionality into common functions.  That's why you hvae them.  Generally, if you see yourself writing the same code twice, you should probably be looking for a way to unify them.  Note that the 80/20 rule applies here, so don't go overboard (one line may not be a good candidate, for example).  Also, python is duck-typed which leads for extra opportunities for this sort of refactoring, but can lead to more confusing code.[*]Make sure to properly encapsulate data.  If something can operate on a class usely solely the public interface, it should be a non-member function.[*]Make your interfaces easy to use and hard to break.  Pretend someone who doesn't code at all is writing code using your classes and functions.  Design it so he'll be able to use it.  Generally, this line of thinking leads to better code.[*]If you don't understand something, write it down.[/list]

---

### Post by engla on 2006-03-15
I had a neat chat about unit testing in #python yesterday. I'm very much a learner, but others were working on large projects or doing programming for a living.
All agreed that unit testing can be very useful, and we discussed it pretty much without being python-specific.
There are some things
# Write tests before writing the actual code, this way the tests are part of the spec that tells you which parts of the "contract" you have fulfilled
# Witing the skeleton of a class and the tests for it at the same time helps you to think about the design of the application and the role of the class

---

### Post by thumper on 2006-03-15
**krypto_wizard** most design skills just come from practice and discussions with more experienced developers.  Even reading the best books or papers on design doesn't end up giving you the skills that you get from working one on one with a mentor.

If you are wanting to discuss something in particular without wanting to post publicly, you have my email address.

---

### Post by LordHunter317 on 2006-03-15
[QUOTE=engla]# Write tests before writing the actual code, this way the tests are part of the spec that tells you which parts of the "contract" you have fulfilled[/quote]I think it's better to say, "Write test to the sepecification," (when you have one).  I'm not sure the when is important.  The XP practice of writing code to the tests doesn't work, IME.  Both should be written directly from the specification.

When you don't have a spec, you should write tests for two cases:[list][*]Behaviors you know are correct.  An example: throwing ArgumentNullException when a null argument is passed that cannot be null[*]Behaviors you want to perserve, at least for now.[/list]

---

### Post by Dml on 2006-03-15
Another tip: writing code and then commenting it can be necessary, but it is much better to first clearly write what result this piece of code should have, and then write the code. It's sort of specification, but you really just write it as comment then write piece of code right after writing it while ideas is still fresh in head. When writing what it should do you may realize that it should be say split into parts, or something like that.

---

### Post by thumper on 2006-03-15
Another small piece of advice:
   don't wait too long before running code

Even if most of the functionality is stubbed out, run the program and make sure it does what you expect - even if it just says:
   TODO: add this function
   TODO: add that function
   etc

Add bits and rerun.  It lets you know when things break.

A more agile approach is to write some tests for what you code should do and how it should behave.  Initially your code will fail the tests - normally because you haven't written it yet.  As you implement your code keep running the tests on it.  One by one you will get the tests passing.  Once everthing passes - your finished (assuming that your tests were sufficient :) ).

---

### Post by mlind on 2006-03-15
I have the obvious, If it's not broken, don't fix it. :mrgreen: 

* Design before you get kneep deep in coding. It does actually save quite lot of time
* Try to apply the coding conventions for each language you use
* Comment your methods/functions before it's too late
* Put up a cvs or svn repository. Just in case.

As for java coding
* Don't throw an exception, catch it
* Don't catch a runtime exception. You're probably screwed anyway. (Nowdays this doesn't count anymore)
* Prefer event driven design
* Always code on interfaces. Always.
* When writing an app. Write stubs for testing the functionality. JUnit is great.

and last but not least. UML modelling is not for pussies.

---

### Post by LordHunter317 on 2006-03-15
Catching runtime exceptions is perfectly permissible in a whole host of situations (and most of the exceptions that are checked really ought to be RuntimeExceptions anyway, but that's another story).

Preferring event-driven design in Java is a ludcriously bad idea.  Event handling in Java is poor by both design and convention and it's always bad to force event-driven design where it doesn't apply.  SAX is my favorite example of this: XML parsing shouldn't be done in an event-driven manner.  What other sort of file have we ever parsed like that?

[edit]I should clarify and say that when it is correct to use it, of course it should be used.  But it certainly shouldn't be preferred, in Java at least.

As for coding for interfaces, that's also a bad idea.  I submit AWT and Swing as perfect examples: the Listener/Adapter case.

One should define interfaces or abstract classes as appropraite and as design warrants.  Many programs simpy using the Java class libraries will never need to define an interface.

---

### Post by mlind on 2006-03-15
I thought that someone would share an opinion :mrgreen: 
Thanks!

[QUOTE=LordHunter317]Catching runtime exceptions is perfectly permissible in a whole host of situations (and most of the exceptions that are checked really ought to be RuntimeExceptions anyway, but that's another story).
[/QUOTE]

That's what I said. But you *really* need to know what you're doing and at least
comment why you're doing so. Many new coders start catching NullPointers or
ArrayOutOfBoundExceptions for instance, without knowing that their code is
bugged. That's maybe a bad example, but valid one.

I've always used exceptions to signal that something is very badly wrong, maybe
recoverable, usually fatal, but definetly something needs to be done. And fast.


Now, for runtime exceptions, I must admit I'm a big fan of them :) 
When Hibernate and other mainstream j2ee frameworks were moving towards
RuntimeException philosophy, I was thrilled. No more ugly try-catch blocks where
they shouldn't even be. Code stays clean and less erroreus. And  when
RuntimeException is thrown, at least my interceptors know it's time to try 
to save the sunking ship..

There are always fans of both ways. I prefer unchecked exceptions.


[QUOTE=LordHunter317]
Preferring event-driven design in Java is a ludcriously bad idea.  Event handling in Java is poor by both design and convention and it's always bad to force event-driven design where it doesn't apply.  SAX is my favorite example of this: XML parsing shouldn't be done in an event-driven manner.  What other sort of file have we ever parsed like that?
[/QUOTE]

Event driven aspect may simplify your application in great detail, but it can be a
burden when used in wrong context, SAX may be one bad example. From my
experience event driven model has always been win-win choice compared to
polling priorityqueue, etc implementations. Yet, this model is very easy to
implement using one interface and couple classes. 


[QUOTE=LordHunter317]
As for coding for interfaces, that's also a bad idea.  I submit AWT and Swing as perfect examples: the Listener/Adapter case.
[/QUOTE]

AWT is a joke, but if you say coding on interfaces is a bad idea, I can't take you
seriously. Have you participated on developing larger scale applications that
rely on the interfaces you or some other third party has designed?
Or when framework offers you to just a interface to implement to get functionaly
that would otherwise be quite a pain? Isn't AOP and dynamic proxing like CGLIB
based on (entirely) interfaces? With interfaces you abtract the actual
implementation, I may be wrong but I see this as a huge benefit.
I think I somehow missed your point on this?



[QUOTE=LordHunter317]
One should define interfaces or abstract classes as appropraite and as design warrants.  Many programs simpy using the Java class libraries will never need to define an interface.[/QUOTE]

That is very true. Interfaces don't belong everywhere. Just don't hesitate to
use them. I usually always design my applications on interfaces, before I do
the actual implementation. But that's just me, I've been taught to design this
way.

---

### Post by LordHunter317 on 2006-03-15
[QUOTE=mlind]That's what I said.[/quote]No, it isn't.  RuntimeExceptions cover more than the exceptions you're thinking of.

> But you *really* need to know what you're doing and at least
comment why you're doing so. Many new coders start catching NullPointers or
ArrayOutOfBoundExceptions for instance, without knowing that their code is
bugged. That's maybe a bad example, but valid one.Yes, it is a poor example because it's not indictiative of all cases of RuntimeExceptions.

What's probably correct to say is that one shouldn't be catching an exception in the first place unless:[list][*]The exception can be expected to occur (i.e., if talking to the database, the possibility of a database error can occur)[*]The exception can be handled.[/list]If both conditions can't be met, the exception shouldn't be caught.

> I've always used exceptions to signal that something is very badly wrong, maybe
recoverable, usually fatal, but definetly something needs to be done. And fast.Exceptions should be used to signal exceptional events.  No more meaning should be applied to them, but certainly no less.

> Event driven aspect may simplify your application in great detail, but it can be a
burden when used in wrong context, SAX may be one bad example.SAX is the perfect example of applying a particular design model where it isn't warranted.

>  From my
experience event driven model has always been win-win choice compared to
polling priorityqueue, etc implementations.Well, it's still situation dependent. 

The point is, **one shouldn't *prefer* anydesign model *over another***.  One should use whatever model is most appropriate in the situation.   That may be an event-driven system.  It may be a queue-based system with notification events.  It may not use events at all, it may be strictly procedural in nature.

It may be a continually running state machine.  

My issue isn't with suggesting that event-driven design should be used, but that it should be preferred.  It shouldn't be preferred unless it's warranted in the situation.  Many situations do not call for it in the least.

> AWT is a joke, but if you say coding on interfaces is a bad idea, I can't take you
seriously.When it is inappropriate, it is a bad idea.  It's adding code and complication for no gain.

>  Have you participated on developing larger scale applications that
rely on the interfaces you or some other third party has designed?Yes, in several languages.

> Or when framework offers you to just a interface to implement to get functionaly
that would otherwise be quite a pain?This seems to be a non-sequitur.  I'm not sure what you're trying to say here.

> With interfaces you abtract the actual
implementation, I may be wrong but I see this as a huge benefit.
I think I somehow missed your point on this?When it is appropriate, it is a huge benefit.  However, not all situations call for it.  Classes modeling data stored in database probably don't have any behaviors that should be modeled in an interface or any other ABC (Abstract Base Case, I'll generalize from now on).

Why?  Because there's only one form of "User" in the database and that model is concrete.  Why abstract out the behaviors when there is only ever one implementation.

Generally speaking, to require an ABC of any sort, you must met the following conditions:[list][*]You must have a common set of behaviors with different implementations.[*]You require the ability to call the behavior through a single code path.[/list]Both are requirements to need an ABC.

I'll give examples of cases with both tests are failed and why an ABC isn't warranted.

For the first one, my database model classes are a good example.  I have to model sales orders, but there's only one kind of sales order in the database.  As such, no matter what, there can only be one correct implementation in the code.  As such, there's no need for an interface because the set of behaviors that are being modeled is implied in the class definition.  The interface is purely redundant, it does not tell us anything we don't know from the class definition.  IOW, there is no need for an ABC because there is no abstraction occuring.

For the second one, let's consider database objects again.  We can operate under the assumption that we're going to have to be able to read them from the database at some point and also under the assumption we will have to save at least some of them at some point.  This is a common behavior, and thus mets criteria one.

However, we don't need to call the save functionality for each different class through the same interface.  I may modify the information about a sales order and not even load any of the lineitems related to it.  I may also do the opposite.

In either case however, I don't gain anything from being able to pass either as  an instance of Saveable or anything of the sort.  The code working with a sales order or a lineitem already knows the type of the object, so you already know all the behaviors the class supports directly.  Making them implement Saveable doesn't gain me anything I don't already know.  IOW, no ABC is required because no polymorphism is going on.

As an example of where it is warranted, consider I'm storing these objects in a cache and I want to persist the cache somewhere, possibily for reloading later or for debugging purposes.  In this case, all I care about is the ability to save the object, so an interface is warranted.  I have a common behavior, and I have a common path for calling the behavior, regardless of type.

This brings me to a general guiding rule for telling if an ABC is needed: If all you're interested in a solely specific set of behaviors and nothing else (i.e., all you care about is the ability to call Save(), or call JumpUpAndDown() regardless of what else the class can do) then an ABC is warranted.  This isn't a universally applicable guideline, but it works in most cases.

> That is very true. Interfaces don't belong everywhere. Just don't hesitate to
use them. I usually always design my applications on interfaces, before I do
the actual implementation. But that's just me, I've been taught to design this
way.It's usually eaiser to see them after the fact.  You only have to design them ahead of time when the need to provide a fixed API is a concern.    This isn't most code.

---

### Post by mlind on 2006-03-15
lol, thanks for prompt response :)
Your points were very good, gave me few pointers to consider in the future.
I hope this won't go too much off topic.


[QUOTE=LordHunter317]
RuntimeExceptions cover more than the 
exceptions you're thinking of.
[/QUOTE]

I guess know how the hierarchy goes, unless there's been something
groundbreaking lately. It wasn't my intent to cover the whole subject,
just to point out general abuse of the exception model.

[QUOTE=LordHunter317]
What's probably correct to say is that one shouldn't be catching an exception in the first place unless:[list][*]The exception can be expected to occur (i.e., if talking to the database, the possibility of a database error can occur)[*]The exception can be handled.[/list]If both conditions can't be met, the exception shouldn't be caught.
[/QUOTE]

exacty, well said.


[QUOTE=LordHunter317]
Exceptions should be used to signal exceptional events.  No more meaning should be applied to them, but certainly no less.
[/QUOTE]

I agree.


[QUOTE=LordHunter317]
This seems to be a non-sequitur.  I'm not sure what you're trying to say here.
[/QUOTE]

Well, my mind was filled with how decorator design pattern is applied on AOP
frameworks. Just by implementing something like MethodInvocation interface
you get whole set of functionaly which would otherwise be somewhat difficult
to implement.


[QUOTE=LordHunter317]
Why?  Because there's only one form of "User" in the database and that model is concrete.  Why abstract out the behaviors when there is only ever one implementation.

Generally speaking, to require an ABC of any sort, you must met the following conditions:[list][*]You must have a common set of behaviors with different implementations.[*]You require the ability to call the behavior through a single code path.[/list]Both are requirements to need an ABC.
[/QUOTE]

How about common functionality? Let's say your domain object model has Users, Admins and Guests.
You want to use pluggable security framework, something like Acegi and implement some sort of user authentication.
Each of domain object model modules must be distinguished from another, but somehow authenticated like one.
That security framework offers you AuthResource interface with a single method, authenticate. You make your
DOM modules implement this interface, and now Admins, Users, Guests can all be authenticated and valitated. Just by 
impelemting single interface you have a fully secured authentication. If you happen to need to authenticate a StaffMember too, you know the drill.

Even if implementation is one, it's possible to introduce functionality that hasn't got anything to do with database
model or modules persistent state. From databases view domain model may stay concrete, but required (new) functionality is
ofter added through interfaces.

If you've played with ORB bridges like Hibernate, you know that by using even a marker interface or
abstract base class you can effectively query objects of just that type. Let's say your User has a name
and he owns a Dog that has a name. They both implement the NamedEntity interface. By issuing query aganist
database using the interface as a query parameter, you'll get implementations of that interface, but you don't
want to/need to know their concrete class, you just need to know it has name so you can display it on screen.




[QUOTE=LordHunter317]
For the first one, my database model classes are a good example.  I have to model sales orders, but there's only one kind of sales order in the database.  As such, no matter what, there can only be one correct implementation in the code.  As such, there's no need for an interface because the set of behaviors that are being modeled is implied in the class definition.  The interface is purely redundant, it does not tell us anything we don't know from the class definition.  IOW, there is no need for an ABC because there is no abstraction occuring.
[/QUOTE]

Let's look that sales order. Your management staff wants to collect reports about sales orders, customers, meetings and
other interactivity which they don't even actually know theirselves. They just announce that everyone
implementing Reportable is going to leave their reports about recent activity at the end of the day.
Then sales orders, customers, etc.. begin to flow in direction of database, but before that - an interceptor watching for Reportables caughts each one at time and adds timestamps to their reports. Finally, all Reportables are commited to database on a huge batch update.




[QUOTE=LordHunter317]
For the second one, let's consider database objects again.  We can operate under the assumption that we're going to have to be able to read them from the database at some point and also under the assumption we will have to save at least some of them at some point.  This is a common behavior, and thus mets criteria one.

However, we don't need to call the save functionality for each different class through the same interface.  I may modify the information about a sales order and not even load any of the lineitems related to it.  I may also do the opposite.

In either case however, I don't gain anything from being able to pass either as  an instance of Saveable or anything of the sort.  The code working with a sales order or a lineitem already knows the type of the object, so you already know all the behaviors the class supports directly.  Making them implement Saveable doesn't gain me anything I don't already know.  IOW, no ABC is required because no polymorphism is going on.
[/QUOTE]

I guess this depends how design the database access layer or you domain model. I'm fan of DAO pattern that simplifies the access by abstracting the database layer as a set of interfaces. Interfaces range from generic to specific, but every implementation is based on a interface or on multiple interaces. This simplfies the code on other layers, because I can call a certain interface without knowing the actual concrete class. I gain more than a lot as design-wise if I pass a instance of Persistent interface to a dao implementing GenericDAO for saving it to database. Actually my other layers communicate only through interfaces.

---

### Post by LordHunter317 on 2006-03-16
> How about common functionality? Let's say your domain object model has Users, Admins and Guests.
You want to use pluggable security framework, something like Acegi and implement some sort of user authentication.
Each of domain object model modules must be distinguished from another, but somehow authenticated like one.Roles and groups are usually handled as enumerations or bits.  The common functionality is external, and I could just as easily hand them another object.

> That security framework offers you AuthResource interface with a single method, authenticate. You make your
DOM modules implement this interface, and now Admins, Users, Guests can all be authenticated and valitated. Just by 
impelemting single interface you have a fully secured authentication. If you happen to need to authenticate a StaffMember too, you know the drill.I'd quite likely make it a seperate class if the interface was like this.  Security is complicated to warrant a class of it's own, and I know for a fact that's a insufficent interface.

> Even if implementation is one, it's possible to introduce functionality that hasn't got anything to do with database
model or modules persistent state.Occasionally, but generally that belongs externally.

> If you've played with ORB bridges like Hibernate, you know that by using even a marker interface or
abstract base class you can effectively query objects of just that type. Let's say your User has a name
and he owns a Dog that has a name. They both implement the NamedEntity interface. By issuing query aganist
database using the interface as a query parameter, you'll get implementations of that interface, but you don't
want to/need to know their concrete class, you just need to know it has name so you can display it on screen.The number of cases where a situation like that is true are pretty small though.  At that point, I know the entry in the database is a string and I'd just as soon use that as a type.  The abstraction certainly isn't gaining me anything.



> I guess this depends how design the database access layer or you domain model. I'm fan of DAO pattern that simplifies the access by abstracting the database layer as a set of interfaces.It almost never does for your *model* objects, unless you have functionality they must support external to the database.  For the process of saving/loading data, it never does unless you're doing polymorphic serialization.  The value of this is somewhat questionable.

> This simplfies the code on other layers, because I can call a certain interface without knowing the actual concrete class.My point is, you probably actually already know the concrete class in all cases anyway.  There's only one possibly concrete class it could be on most webpages.

> I gain more than a lot as design-wise if I pass a instance of Persistent interface to a dao implementing GenericDAO for saving it to database.What do you actually gain?  When do you ever deal with multiple instances of Persistent objects simulataneously?

---

