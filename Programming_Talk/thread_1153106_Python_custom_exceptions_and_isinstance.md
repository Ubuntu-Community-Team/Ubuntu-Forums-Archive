---
title: "Python custom exceptions and isinstance"
date: 2009-05-08
forum: Programming Talk
---

### Post by Flimm on 2009-05-08
I've defined a bunch of custom python Exceptions in a module, and import them in my program whenever I need them. One of my functions attempts to load several files in succession, and instead of raising a custom Exception at the first error, I though I'd return a list of Exceptions instead, one Exception for each error. Then I handle each exception one by one afterwards.
So I've got something like this:
[php]content, exceptions = load_files(path)
for excp in exceptions:
    if isinstance(excp, custom_exceptions.MyCustomException):
         print "custom exception"
[/php]
The trouble is, isinstance doesn't behave as expected. The ids of excp.__class__ and custom_exceptions.MyCustomException are different. A solution I've found is to compare excp.__class__.__name__ with MyCustomException.__name__, is this dangerous?
How do you handle custom exceptions? Am I crazy to define a custom Exception like this:
[php]class MyCustomException(Exception):
   def __str__(self):
       return "MyCustomException !"
[/php]

---

### Post by nvteighen on 2009-05-08
Ehm... I notice a conceptual confusion in here. Let's see. An exception is an interrupt, this means: it's a way to stop the execution of a routine when some event occurs, usually an error.

So, you should exceptions when you need to interrupt execution. If you just want to pass some information around which you'll "collect" afterwards, you don't need an exception, but a list of error codes (C-style) may be all you need.

The issue with your isinstance is possibly this: raising an Exception involves creating an **instance** of some class (**raise IOError** creates an instance of IOError which you can then refer to if you give it a name in the catching **except** block). So, if you do something along the lines of **[MyCustomException1, MyCustomException2, IOError]**, you're just referring to class names, but not instances... Maybe you should **[MyCustomException1(), MyCustomException2(), IOError()]** (i.e. instantiating instances), so you return anonymous instances, but because again, it sounds really absurd to me to do that...

Your Exception is correctly created, anyway.

---

### Post by dandaman0061 on 2009-05-08
This may be a bit redundant with nvteighen's post but I'll provide a sample.  Are you doing/wanting something like this?

```

def load_files(path):
    exceptions = []
    try:
        if not path:
            raise CustomException1("PATH is empty!")
    except CustomException1, inst:
        exceptions.append(inst)

    try:
        if len(path) > 1234:
            raise CustomException2("PATH is too long!")
    except CustomException2, inst:
        exceptions.append(inst)

    try:
        if not os.path.exists(path):
            raise CustomException3("PATH doesn't exist!")
    except CustomException3, inst:
        exceptions.append(inst)

    #... get file_content in here
    #  could also use the above methodology to generate
    #  warnings about the file

    return file_content, exceptions

```

If so... I would agree with nvteighen that you aren't using Exceptions in the way that they are intended.  Now that isn't always a bad thing to do (thinking outside the box), but it may be clearer to other coders/maintainers/yourself-later if you just append strings to your exceptions list of the 'warnings' that you are creating.  Because handling exceptions in this manner is basically that.  You are logging warnings, where exceptions are generally meant to stop execution. Catch clauses just anticipate what things could go wrong to continue running smoothly or to die gracefully.  IMHO it is best to handle exceptions as they come up one at a time.... did I make any sense?

Anyway, this may not be what you've done

---

### Post by Can+~ on 2009-05-08
And why would you ever need a list of exceptions, when exceptions jump to the except block immediately?

I mean, you've given some thought to it and maybe there's logic behind it, but I can't seem to find it.

---

### Post by Flimm on 2009-10-13
I seem to have the same problem as [this person](http://stackoverflow.com/questions/1063228/custom-python-exception-with-different-include-paths), but I'm not using Django.

---

