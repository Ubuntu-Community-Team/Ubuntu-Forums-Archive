---
title: "Software engineering - How to design a software to support plugins?"
date: 2010-05-17
forum: Programming Talk
---

### Post by sheperson on 2010-05-17
Hi,
I have developed several applications and web sites so far. But I have always been thinking about how to design a software to support plug-ins?

For example:
If I want to develop a web site, I want to make the basic structure per project. Then for other common parts like user management, searching, downloading and etc. design re-usable components and use them each time like plug-ins. I know it is hard to achieve this completely but it would be great to achieve even partly.

Does anyone have any ideas? Any guides, books or resources?
Thanks in advance.

---

### Post by soltanis on 2010-05-17
It is really simple. What you do is you offer an API for plug-ins to use. So whatever your site does, you should make a way for other scripts and things to come in and use that information to present it a different way, i.e. if you have routines for accessing some database information given some credentials, you should make them publicly available and document them. People will then be able to write their own application subsets that process the data differently.

Another way to do it is through the use of something called callback functions. You can create an API method for other scripts to "register" themselves as plugins, and during a certain stage of processing in your program, you would invoke a function in the external script and pass it some data, then later, collect the data back. This way, you enable external functionality.

To see what I mean, take this Python code:

```

# method 1: create a public API

class Dummy:
'''This class does some stuff which I documented well.'''
  def __init__(self, one, two):
    self.one = one
    self.two = two
  
  def do_processing(self):
    process(self.one, self.two)

# now you would expose this API to other applications, i.e. on a website, you would have a way for other scripts to create and manipulate your objects as they would a library.

# method 2: create callbacks (also with a public API)
def big_processing_task(one, two, three):
  for callback in callback_table:
    (one, two, three) = callback(one, two, three)
  # the external functions processed your data, now finish processing
  return finish_him(one, two, three)

```

Probably not the clearest of examples.

If you gave me some more context as to what language you're using and in what kind of program you're doing this I can clarify it more.

---

### Post by sheperson on 2010-05-17
Hi,
Thanks for your reply.
> **soltanis said:**
> 
Probably not the clearest of examples.

Good point :confused:

> **soltanis said:**
> 
If you gave me some more context as to what language you're using and in  what kind of program you're doing this I can clarify it more.
Well, I program both in Java and C# (.Net), mostly C#, mostly web sites. But I do applications too, but not often.

Thanks again for the help.

P.S: If you could tell me any books, tutorials I would be very thankful.

---

### Post by Some Penguin on 2010-05-17
In Java, you can use the Class.forName() to load a class (at run time!), use the Class object's methods to get a constructor if you want to use instance methods instead of static methods, and use the various reflection APIs to obtain references to individual methods and the like.

Best if you can verify that the class implements a specific interface or set of interfaces that you have in mind (see Class's 'isAssignableFrom' and 'isInstance', for instance), so you can cast it and use it that way rather than interrogating it via reflection, of course.

---

### Post by r-senior on 2010-05-17
Have a look for examples of the Strategy design pattern and the Observer design pattern. These are essentially the design patterns that formalise the principles that soltanis describes.

The Wikipedia pages have examples in various languages:

[http://en.wikipedia.org/wiki/Strategy_pattern]("http://en.wikipedia.org/wiki/Strategy_pattern")

[http://en.wikipedia.org/wiki/Observer_pattern]("http://en.wikipedia.org/wiki/Observer_pattern")

---

### Post by JwB Zoofware on 2010-05-17
> **Some Penguin said:**
> In Java, you can use the Class.forName() to load a class (at run time!), use the Class object's methods to get a constructor if you want to use instance methods instead of static methods, and use the various reflection APIs to obtain references to individual methods and the like.

Best if you can verify that the class implements a specific interface or set of interfaces that you have in mind (see Class's 'isAssignableFrom' and 'isInstance', for instance), so you can cast it and use it that way rather than interrogating it via reflection, of course.

Pretty much the same as in C#. Create a few interfaces for the functionality you want to expose, and then classes that implement them can be loaded from a separate assembly at runtime.

[http://blogs.msdn.com/abhinaba/archive/2005/11/14/492458.aspx](http://blogs.msdn.com/abhinaba/archive/2005/11/14/492458.aspx) is a rough example.

---

### Post by phrostbyte on 2010-05-18
Basically you use a technique called "reflection" to implement a plugin framework.

Java has the Java Plugin Framework and .NET has the Managed Extensibility API. They offer some high level wrapper around reflection to support plugins in your applications.

You can even do this in pure C/C++ using the low level dlopen() and dlsym() functions in ld.so

---

### Post by sheperson on 2010-05-18
Hi,
Thank you all, for your replies.
After your posts and after searching in Google I came up with the idea of Component Oriented Programming. I think it does what I want (I am not sure yet, I should work more on it), correct me if I am wrong, please.

And I have got [this book]("http://www.amazon.com/Component-Oriented-Programming-Andy-Ju-Wang/dp/0471644463") and I am working on it.
Thanks again.

---

