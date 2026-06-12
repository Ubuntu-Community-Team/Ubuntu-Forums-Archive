---
title: "Separating functionality from UI"
date: 2009-07-20
forum: Programming Talk
---

### Post by jero3n on 2009-07-20
I am writing some statistics software in C. I am thinking of writing the UI in another language like C# and I would also like to expose the functionality of the engine to other programs. Most of the communication between the engine and the UI is in the form:

-UI sends a query to the engine for some function
-UI might send a large matrix of data within the query
-Engine begins calculations and reports to the UI the progress until it finishes and post a reply
-UI might ask engine to cancel before completion
-Engine should stay alive and keep previews results in memory in order to reply to further queries

There are various ways to implement this. I could build the engine as a .dll in windows or .so in Linux but, correct me if I am wrong, it is not portable solution. I wish to avoid it. Or I could build the engine as a separate executable and make communication through TCP/IP but I think it gets very complicated for what I want to do.

Is there any better general idea? Is there any other similar project from which I could get some ideas?

---

### Post by cb951303 on 2009-07-20
Although I don't have personal experience with it, I know a lot of applications use [XML-RPC]("http://en.wikipedia.org/wiki/XML-RPC") for communication between engine and frontend.

---

### Post by fr4nko on 2009-07-20
I think that this is a very good idea. It is a very elegant solution that is viable only if the interaction between the UI and the engine is not too much tight. I've used myself this approach for two application, one in ocaml and another one in C/C++.

I believe that also Mathematica from Wolfram Research is implemented like that.

My application in C/C++ performs some numerical calculations and the engine is implemented in C. The interface for the other side is implemented in C++ and they interact by using a  set of API. So actually the separation is not very well defined and I'm planning to improve that by separating better the two components.

Talking about the implementation, I believe that you don't need to make two separate executables, neither to produce a shared library, you can simply link together the applications that will communicate with each other through a normal C interface. In fact I believe that the advantage of separating the engine and the UI is only for the programmer, for the design. At run-time it will make no difference and it will be faster if they are linked together. Also you can avoid all the complication of asyncronous communication.
To separate the engine and the UI will be useful only if you believe that the UI can crash and you want to run them as separate processes.

One of the key design aspect is: how the engine will provide the results to the UI ? this is a critical point because often the results can be complex data structures. A sub-optimal design can also bring to some unnecessary data duplication between UI and the engine so you have to think carefully about this point.

Something also important is to choose the correct level of granularity in the communications between the engine and the UI. My advice is to define the rough line of the interface before starting to code anything.

I would like to add that one advantage of this kind of design with separation between the engine and the UI is a better facility to optimise and debug your code. In fact you can fine tune your engine without worrying about the complexity of the UI. For example you can write a very simple text UI to debug and optimise easily your engine or may be use valgrind on it to detct memory leak.

So, good luck with your software.

Francesco

---

### Post by leblancmeneses on 2009-07-20
separating functionality from ui is solved through model view presenter in todays standards.


your asking for seperating services and are dealing with service oriented architecture.


if you want easy solution you need to be on ms platform with wcf ...  on your linux client you need to create manually a service proxy since .net code generation won't build a non ms platform proxy it normally creates when you reference a wcf service.


DIY approach is like you already mentioned brute force all layers with manual work.    If you forsee this project getting big you might want to look into dsl and create a language maybe something like IDL and transform (code generate) both sides.

---

### Post by jero3n on 2009-07-20
Thanks for your suggestions.

I have to look into these deeper, however it seems I cannot avoid a complicated solution :)

Francesco:
> you can simply link together the applications that will communicate with each other through a normal C interface
This was my first thought, but I would like to use the "engine" dynamically, from languages other than C/C++ without the need of bindings.

---

### Post by fr4nko on 2009-07-21
> **jero3n said:**
> Thanks for your suggestions.

I have to look into these deeper, however it seems I cannot avoid a complicated solution :)

Francesco:

This was my first thought, but I would like to use the "engine" dynamically, from languages other than C/C++ without the need of bindings.
I see, but you still can use the C API since

[LIST]
[*]every programming language is able to interface with C
[*](almost) every programming language can be linked with C compiled files (object files or library)
[/LIST]
don't complicate things unless if it is absolutely necessary :-)
otherwise you can do something fancy with communication through sockets but this will be a lot of additional work and I don't really see the benefit.

Francesco

---

### Post by jero3n on 2009-07-21
> don't complicate things unless if it is absolutely necessary

Yes, I guess you are correct :)

---

