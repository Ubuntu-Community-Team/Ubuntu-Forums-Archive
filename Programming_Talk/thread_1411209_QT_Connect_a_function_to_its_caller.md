---
title: "QT: Connect a function to its caller?"
date: 2010-02-19
forum: Programming Talk
---

### Post by Zorgoth on 2010-02-19
I am designing my first sophisticated GUI and I am trying to design an error handling system that will respond differently based on who called it and where it was called; I am currently thinking of connecting functions where error handling is necessary to their callers (well, connecting objects that are created by functions) with their errors as signals to be received by the caller so it can take appropriate action and possibly talk back to the function (perhaps by editing values stored inside itself; perhaps I should create a class that can handle broad ranges of values of this kind if this is necessary so that only one error handling object has to be declared in each class?).  

So what I need to know is either, is there a better way than this to handle errors, or, how do I identify the caller of the function from within the function?  Will I have to pass it as an argument or is there a better way?  Or should I have a registry of who is calling functions?  Or is there a built-in way to do it?  

I haven't done much coding yet so whatever the best system is I can implement it from the bottom up.

---

### Post by Simon17 on 2010-02-20
It sounds like you're talking about something similar to exceptions.

Is there some reason you don't want to use exceptions?

---

### Post by Zorgoth on 2010-03-01
I didn't really know much about exceptions when I wrote this.  So, seeing this, I have a few questions.  

Are there standard sorts of functions that are going to interfere with my exception handling (for example by throwing exceptions of their own that I might not want to catch with my own handlers)?

Would it be better in general to write functions that always throw exceptions and always be ready to handle them or to pass to the function information on what kind of exceptions it can throw (with default values of false), in which case the function would perform some default method of error handling?

And why is it that some people (e.g. Google Style Guide) prefer return codes to exceptions?

---

### Post by Simon17 on 2010-03-01
Yes, the standard library can throw exceptions, however you don't have to catch them if you don't want to. You specify the type (and subtypes) of exception that you want to handle.

Ultimately, I think it's better to have a choice (though that's only my opinion. Others will disagree). C++ gives you a choice, but the default is "true". For example, "new" by default will throw an exception if it can't allocate memory, but the nothrow version returns a null pointer.

One reason is that using exceptions incorrectly can cause memory leaks. You could argue that if designed properly, using return values or other error codes is simpler than exceptions though. Exceptions are definitely better where error handling is put in as an afterthought.

Another reason most people like exceptions is because it's easy to consolidate your error handling code into one place and because lazy programmers don't bother to check return values.

---

