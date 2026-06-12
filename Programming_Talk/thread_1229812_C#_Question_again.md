---
title: "C# Question again"
date: 2009-08-02
forum: Programming Talk
---

### Post by Mirge on 2009-08-02
I built a simple calculator as a learning exercise, and I learned a good bit as I went along without really planning it out at first.

By the time I was done, I found that my code was pretty cluttered, and I didn't like it.

How do I go about separating out maybe sets of methods into separate .cs source files and being able to use them in event handlers, etc?

IE:

1 form with 1 button that says "click me", and is named "button1"... I set an event handler for button1 that goes to a method called button1_Click(object sender, EventArgs e) { ... }

Inside of button1_Click(...) I'd like to be able to call a function defined in another source file.. how would I go about doing that? jero3n where are u :) .... thanks!

---

### Post by Can+~ on 2009-08-02
Long time without using C#, but I remember you can use the "Partial" keyword to split a class across multiple source files.

[http://msdn.microsoft.com/en-us/library/wa80x488(VS.80).aspx](http://msdn.microsoft.com/en-us/library/wa80x488(VS.80).aspx)

---

### Post by Mirge on 2009-08-02
> **Can+~ said:**
> Long time without using C#, but I remember you can use the "Partial" keyword to split a class across multiple source files.

[http://msdn.microsoft.com/en-us/library/wa80x488(VS.80).aspx]("http://msdn.microsoft.com/en-us/library/wa80x488%28VS.80%29.aspx")

Ahh that is exactly what I needed. Thanks Can+~ \\:D/

Wrote a quick test program like I mentioned, the event handler is in a separate source file... worked beautifully. Now I will probably rebuild the calculator program... keeping the source a lot cleaner.

---

### Post by doas777 on 2009-08-02
glad that worked. i like partial classes for extending compiletime generated components (datasets and tableadapters and the like) as an alternative to inheriting. 

I would probably have gone another way, and used the default handler names, but had them explicitly call the routine that i want to fire, just because it's easier to read for someone who inherits your code later on (understandably this may not a problem in your case). they look at the codebehind, expecting to find the handler, but it doesn't appear to be there. so eventually they're searching the solution for  whatever file that the partial class is defined in. if you use good naming conventions, it shouldn't be too hard, but still, it saves people time when maintaining your code. just my 2 bits.

have fun,
franklin

---

### Post by Mirge on 2009-08-02
> **doas777 said:**
> glad that worked. i like partial classes for extending compiletime generated components (datasets and tableadapters and the like) as an alternative to inheriting. 

I would probably have gone another way, and used the default handler names, but had them explicitly call the routine that i want to fire, just because it's easier to read for someone who inherits your code later on (understandably this may not a problem in your case). they look at the codebehind, expecting to find the handler, but it doesn't appear to be there. so eventually they're searching the solution for  whatever file that the partial class is defined in. if you use good naming conventions, it shouldn't be too hard, but still, it saves people time when maintaining your code. just my 2 bits.

have fun,
franklin


That is true too. Being a C# beginner, I'm not entirely familiar with the "C# way of doing things" just yet :).

Maybe I'll experiment some more and leave the handlers where they are, but put the methods in a different source file. Lets see if I can figure it out :). Thank you!

---

### Post by jero3n on 2009-08-02
> 1 form with 1 button that says "click me", and is named "button1"... I set an event handler for button1 that goes to a method called button1_Click(object sender, EventArgs e) { ... }

Inside of button1_Click(...) I'd like to be able to call a function defined in another source file.. how would I go about doing that? jero3n where are u .... thanks!
I generally don't like partial keyword. Sounds like the goto keyword: something might went wrong in your design, but a few times it seems a good idea. For example visual studio uses partial classes to separate auto-generated code from user's code.

In your case it seems that you want to separate UI and events from your program's logic. I would made a new class with that "logic" and made an instance object in the form's code. Anyway it's just an opinion.

---

### Post by doas777 on 2009-08-02
> **Mirge said:**
> That is true too. Being a C# beginner, I'm not entirely familiar with the "C# way of doing things" just yet :).

Maybe I'll experiment some more and leave the handlers where they are, but put the methods in a different source file. Lets see if I can figure it out :). Thank you!

or even in a separate library. Usually my goal is separate the front and back-ends as much as possible (especially in java, so i can switch from SWING to SWT easily). if you wanna give your desktop app a web interface, just import the backend, and write your UI. 

if your interested in architechure stuff, look into Nteir design, and SOA.
[http://en.wikipedia.org/wiki/Multitier_architecture](http://en.wikipedia.org/wiki/Multitier_architecture)
[http://en.wikipedia.org/wiki/Service-oriented_architecture](http://en.wikipedia.org/wiki/Service-oriented_architecture)

best regards

---

