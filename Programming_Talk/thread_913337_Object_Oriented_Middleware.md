---
title: "Object Oriented Middleware"
date: 2008-09-07
forum: Programming Talk
---

### Post by MaindotC on 2008-09-07
I'm reading this book:

IT Architectures and Middleware: Strategies for Building Large, Integrated Systems (Unisys Series) (ISBN: 0201709074) by Britton & Bye

and in Ch 3 it talks about OO middleware and Component Modules (M$oft's COM+).  The book talks about 4 different types of server objects:

Proxy Objects
Agent Objects
Entrypoint Objects
Callback objects

Being a non-programmer, I'm trying to understand these concepts.  Tell me if I'm missing the target (quotes are from the book followed by my interpretations) and an example if you can provide one:

Proxy Object - "stands in for an object".  In the line of code:
```

AccountSet.GetAccount return AccountRef

```
AccountRef is the proxy object.  It is a reference to a return value that can replace any calls to AccountSet.GetAccount.

Agent Objects - "providing an agent on the server that acts on the clients behalf."  An Iterator - the agent object knows that the client will have to navigate through rows and indexes of records, so instead of making the client call that procedure each time a row is updated, the Iterator does it automatically and returns the final result to the client.

Entrypoint Object - "an object for finding other objects".  In VB Studio, when you type in an object, it auto-populates with subroutines or procedures that can be accessed through the Entrypoint, or patriarchical, object.

Call-back objects - "reverse interface from server to client, so the server can send unsolicited data...For instance, GUI Buttons, Lists, and Text input fields are all types of controls in Windows and controls fire events."  I can't recall precisely what an event is - I think it's the behaviour of the function based on the input parameters.  I'm still really unclear on what a call-back is.

I appreciate your interpretations and please suggest any links that I can better understand this.  The wikis just aren't cutting it for me.

---

