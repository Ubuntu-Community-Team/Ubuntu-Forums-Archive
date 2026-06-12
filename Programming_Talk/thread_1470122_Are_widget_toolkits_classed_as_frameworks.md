---
title: "Are widget toolkits classed as frameworks?"
date: 2010-05-02
forum: Programming Talk
---

### Post by -etftw on 2010-05-02
Hello,

I am currently doing a bit of research regarding frameworks and I was just wondering if widget toolkits such as GTK+ are classed as frameworks?

My understanding of the definition of a framework is that it defines the low level structure of an application and allows the developer to concentrate more on implementing their design, thus I'd imagine something like GTK+ is a framework as it would take away the need to work with a lower level means of developing UIs and would allow for easier cross platform development.

Would I be correct in my assumption or have I gone way off the tracks?

Any information would be much appreciated.

Thanks

---

### Post by slavik on 2010-05-02
> **-etftw said:**
> Hello,

I am currently doing a bit of research regarding frameworks and I was just wondering if widget toolkits such as GTK+ are classed as frameworks?

My understanding of the definition of a framework is that it defines the low level structure of an application and allows the developer to concentrate more on implementing their design, thus I'd imagine something like GTK+ is a framework as it would take away the need to work with a lower level means of developing UIs and would allow for easier cross platform development.

Would I be correct in my assumption or have I gone way off the tracks?

Any information would be much appreciated.

Thanks
No, it's not.

A framework implements a flow, which a toolkit does not.

with a framework, you write the different components and the framework glues them together, whereas a toolkit, just gives you a bunch of functions/classes to work with.

---

### Post by -etftw on 2010-05-02
> **slavik said:**
> No, it's not.

A framework implements a flow, which a toolkit does not.

with a framework, **you write the different components and the framework glues them togethe**r, whereas a toolkit, just gives you a bunch of functions/classes to work with.

When you say the framework glues them together, would that be like creating events in a .NET application? i.e. you create the event method and then the framework automatically associates the code you created with the appropriate events that are triggered in the application?

---

### Post by slavik on 2010-05-02
> **-etftw said:**
> When you say the framework glues them together, would that be like creating events in a .NET application? i.e. you create the event method and then the framework automatically associates the code you created with the appropriate events that are triggered in the application?
I would say no.

In the same way that GTK's event dispatcher is not a framework.

---

### Post by -etftw on 2010-05-02
Could you give me an example of what you would class as a component?

I understand that frameworks have numerous different components built in, such as the various GUI controls that are at your disposal when building applications in .NET, but I am still unsure as to what makes a framework a framework and not a library.

---

### Post by slavik on 2010-05-02
consider a simple application that is able to fetch data from somewhere (you can write the module for this), it then takes the data and forwards it to the proper interpreter, interpreter processes the data (you can write the module), and then the data can be presented by some presentation module (you can write this as well).

all the data handling from module to module is handled by the "framework."

that's what I understand under framework.

---

### Post by -etftw on 2010-05-02
> **slavik said:**
> consider a simple application that is able to fetch data from somewhere (you can write the module for this), it then takes the data and forwards it to the proper interpreter, interpreter processes the data (you can write the module), and then the data can be presented by some presentation module (you can write this as well).

all the data handling from module to module is handled by the "framework."

that's what I understand under framework.

So even though a framework may come packaged with a number of reusable libraries / components (i.e. the Windows GUI components I mentioned earlier) the main purpose is to provide the developer with a ready to use architecture allowing them to work purely on the implementation of the logic and presentation layers?

---

### Post by soltanis on 2010-05-03
> **-etftw said:**
> So even though a framework may come packaged with a number of reusable libraries / components (i.e. the Windows GUI components I mentioned earlier) the main purpose is to provide the developer with a ready to use architecture allowing them to work purely on the implementation of the logic and presentation layers?

It depends on the "framework". I suppose that I've never really liked frameworks because they lock you into the same basic way of doing things, for example, Django or CodeIgniter. There are also "anti-frameworks" such as web.py which implement a minimalist thing that you can easily extend, but you are free to make many choices as to how you go about doing things (the draw back is you have to implement them yourself).

A widget toolkit like wx does give you a basic workflow of doing things (set up your classes, register events, run the event loop), but in another sense leaves the rest of the program up to you (it focuses on the GUI part).

I've never been bothered by what it's called in the past, though.

---

### Post by slavik on 2010-05-03
> **-etftw said:**
> So even though a framework may come packaged with a number of reusable libraries / components (i.e. the Windows GUI components I mentioned earlier) the main purpose is to provide the developer with a ready to use architecture allowing them to work purely on the implementation of the logic and presentation layers?
with a framework, you usually do not code logic.

Take Netty as an example. You don't alter the code logic, you add resources.

an event dispatcher a framework not make.

[http://en.wiktionary.org/wiki/framework](http://en.wiktionary.org/wiki/framework)
[http://en.wiktionary.org/wiki/toolkit](http://en.wiktionary.org/wiki/toolkit)

I can see how you would consider GTK a framework ... but there is a reason why it's called GNU Tool Kit, instead if GNU FrameWork.

---

### Post by -etftw on 2010-05-03
> **slavik said:**
> with a framework, you usually do not code logic.

Take Netty as an example. You don't alter the code logic, you add resources.

an event dispatcher a framework not make.

[http://en.wiktionary.org/wiki/framework](http://en.wiktionary.org/wiki/framework)
[http://en.wiktionary.org/wiki/toolkit](http://en.wiktionary.org/wiki/toolkit)

I can see how you would consider GTK a framework ... but there is a reason why it's called GNU Tool Kit, instead if GNU FrameWork.

When I say logic I mean the business logic of the application, i.e. if I was creating a calculator program I would code the logic that processes the numbers and operators the user enters; would that be correct?

I think I may understand the definition now of a framework (I hope so anyway), would it be safe to say: "A framework provides a structure that a developer must follow and takes care of the low level interaction between the various layers of the application, such as the transport of data from the model layer to the view layer if the framework was to implement MVC".

That is at the moment the best I can make of it, if I am wrong please feel free to correct though.

Thanks for the help so far too, I think it has helped me progress my definition further :)

---

### Post by nvteighen on 2010-05-03
Just as an anecdote, there's the weird fact that in the Objective-C world, **all** libraries are called "frameworks". That's why Apple Cocoa, which is just a GUI toolkit, is called "Cocoa Framework" and the same goes for all the other various implementations of the OpenStep standard (GNUStep, SideStep, etc.) :P

---

### Post by -etftw on 2010-05-03
> **nvteighen said:**
> Just as an anecdote, there's the weird fact that in the Objective-C world, **all** libraries are called "frameworks". That's why Apple Cocoa, which is just a GUI toolkit, is called "Cocoa Framework" and the same goes for all the other various implementations of the OpenStep standard (GNUStep, SideStep, etc.) :P

I'll make note of that, cheers :)

---

