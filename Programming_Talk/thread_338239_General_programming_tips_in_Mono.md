---
title: "General programming tips in Mono"
date: 2007-01-14
forum: Programming Talk
---

### Post by gynther on 2007-01-14
I'm writing an application in Mono and am having difficulty in the designing(code wise) of the program. It's not a syntactical issue but more on the subject of how to do things properly. This kind of help/tips are very difficult to find and I hope to share from your collective experience.

I've split the application in two typical parts, a library with classes and functionality and the GUI. The issue I have is what do I do with database connectivity in the classes. 

The most obvious is to let each class make a connection and be done with it. But then I'll have several connections that may be active and it feels unnecessary and unwieldy.

Another would be to make a dbClass and use it with all my classes but that seems superfluous and much the same as the one above.

A third could be to make the connection once and share it among the other classes. This makes more sense to me but I don't know how to achieve this.

So, what I'm wondering is; how do you do it? Which way is the most used and/or preferred? If you can give me examples in C#/Mono it's really appreciated.

---

### Post by Grey on 2007-01-14
I'm a C programmer.  I've only used .NET a little bit.  But I think what you are looking for is a singleton.  I'm not really sure how to implement that in .NET.

But how it works is that you write a class that has exactly one instance.  In C++, this is usually achieved by creating a global instance of the class, and never creating another one, or using some tricks to declare the class as static.  I'm sure that something similar exists in .NET.

[http://www.dofactory.com/Patterns/PatternSingleton.aspx](http://www.dofactory.com/Patterns/PatternSingleton.aspx)

There's a link that shows a sample of a singleton in C# though.  Hope it helps.

---

### Post by gynther on 2007-01-14
Thanks! This looks to be what I was looking for. Didn't know it was called Singleton. I'll try this.

---

