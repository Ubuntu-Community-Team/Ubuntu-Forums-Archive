---
title: "[C++] throw() in procedure signatures"
date: 2011-07-22
forum: Programming Talk
---

### Post by nvteighen on 2011-07-22
Hi everyone

I'm not quite fond of C++, as you surely know, but I've been wondering nontheless about a very weird issue related to how you should declare C++ procedures (either functions or methods).

In order to provide full information on how a certain procedure works, C++ allows you to declare what exceptions a certain procedure may throw, like this:

```

int myProc(const myClass&, int) throw(); // No exceptions
int someOtherProc() throw(some_exception); // some_exception
void lastProc(int); // Any exception

```

But nobody uses the first two, not even the C++ Standard Library. I always find procedures declared in the third form, i.e. the one that tells that the procedure might throw any exception, even if it doesn't throw anything at all!

Ok, this feature is a patch over C++ defective type system, compile-time-knowledge obsession and a lot of other things for which we usually quote the "FQA", but given the design of C++ and because you might be forced to use C++ for some reason one day, I'd consider this feature very helpful, like const methods are.

So, could someone please explain me why this feature isn't as good as it seems to me and thus nobody uses it? For the record, does Java has something like this?

---

### Post by psusi on 2011-07-22
It has been a long time since I had to muck with Java, but IIRC, you MUST declare what exceptions every function can throw.  In other words, if you omit the exception list in Java, instead of meaning that anything can be thrown, it means nothing can.

I don't think throw specs are used much because they just don't provide any benefit, and often cause problems when some function you call ends up throwing an exception that you didn't declare in your throw spec, nor handle yourself.

---

### Post by Bachstelze on 2011-07-22
I don't know C++ but I can answer about Java (even though I do not like it, at least this Java course I had to take last semester will be useful for something).

Java has two "kinds" of exceptions. Some are subclasses of either Error or RuntimeException and are sometimes called "implementation exceptions", for example a division by zero or an out-of-bouds array access. Others are subclasses of Exception but not of RuntimeException, and are sometimes called "usage exceptions" (RuntimeException is itself a subclass of Exception, all other subclasses of Exception are "usage exceptions").

The first group of exceptions are considered more serious. They are exceptions that you do not expect to happen in a normal usage of the program, and that you do not throw manually.  Therefore you need not declare that a method might throw them (since they are almost by definiton unexpected).  The second group are exceptions that are thrown, possibly manually with throw(), as a matter of course in a normal execution of the program. They are basically part of the program, so you must declare that a function might throw them.

---

### Post by dwhitney67 on 2011-07-22
> **nvteighen said:**
> 
But nobody uses the first two, not even the C++ Standard Library.

I wouldn't use the word "nobody".  The destructor for std::exception uses the first form.

---

### Post by nvteighen on 2011-07-22
> **dwhitney67 said:**
> I wouldn't use the word "nobody".  The destructor for std::exception uses the first form.

Thanks, but what about everything else?

---

### Post by nvteighen on 2011-07-22
> **psusi said:**
> 
I don't think throw specs are used much because they just don't provide any benefit, and often cause problems when some function you call ends up throwing an exception that you didn't declare in your throw spec, nor handle yourself.

I somehow missed your post before replying to dwhitney67.

Ugh... I don't like how this sounds. So, it boils down to this, as far as I see: if all procedures sticked to this, there'd be no problem because the compiler would always know what throws what and what not... But as soon as you use one procedure that doesn't use an explicit throw() spec, the issue you mention arises.

---

### Post by Simian Man on 2011-07-22
Basically people thought they would be a good idea at the time, but it turns out they weren't.  There are no compelling reasons to use them and several reasons not to.  See [this article]("http://www.gotw.ca/publications/mill22.htm") by Herb Sutter who explains it better than I could.

---

### Post by nvteighen on 2011-07-22
> **Simian Man said:**
> Basically people thought they would be a good idea at the time, but it turns out they weren't.  There are no compelling reasons to use them and several reasons not to.  See [this article]("http://www.gotw.ca/publications/mill22.htm") by Herb Sutter who explains it better than I could.

Thank you so much for the article. Quite convincing and well-explained.

---

