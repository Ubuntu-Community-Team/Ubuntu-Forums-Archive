---
title: "How to develope gui?"
date: 2010-10-28
forum: Programming Talk
---

### Post by tah_206207 on 2010-10-28
hello
I want to develope gui with QT for aria2c ( download manager ) like IDM ( internet download manager for windows ) but i have problems with this!
this software code doesn't documented and i don't know how to read this software codes and start reading this software code from which src file to recognize any object that used in this software code and use this software apis in my gui software.
this software site is :
[http://aria2.sourceforge.net/](http://aria2.sourceforge.net/)
and this software code is in develope tab in site.
please help me to create nice gui internet download manager for linux
thanks alot.

---

### Post by mainerror on 2010-10-28
Sure it is documented. [http://sourceforge.net/apps/trac/aria2/wiki](http://sourceforge.net/apps/trac/aria2/wiki)

---

### Post by tah_206207 on 2010-10-28
Are you sure software code documented?
please show me a src file that is documented
thanks

---

### Post by tah_206207 on 2010-10-28
i am beginner developer please help me how to use this software codes ( because they didn'nt documented! ) 
please tell me about xml-rpc. what's xml-rpc?

---

### Post by Zugzwang on 2010-10-28
As mainerror stated, there is documentation available in the Wiki. An example is the following page: [http://sourceforge.net/apps/trac/aria2/wiki/ArchOverview](http://sourceforge.net/apps/trac/aria2/wiki/ArchOverview) - the architectural overview is a very important document as it tells you something about the overall design of the piece of software. After studying it, whenever you want to modify something, you should be able to identify the parts of the software you will need to touch in order to do so.

For finding out about "xml-rpc", use the respective wikipedia article: [http://en.wikipedia.org/wiki/XMLRPC](http://en.wikipedia.org/wiki/XMLRPC)

Note that many developers do not document class methods if their correct usage is obvious from the context for someone who (1) read the architectural overview and (2) has knowledge of the libraries used. Perhaps this is the case here?

EDIT: Also, the XML-RPC interface [http://aria2.sourceforge.net/aria2c.1.html#_xml_rpc_interface](http://aria2.sourceforge.net/aria2c.1.html#_xml_rpc_interface) seems to be *extremely well* documented. If you don't want to modify the source code for "aria2", there seems to be no necessity to read it.

---

### Post by tah_206207 on 2010-10-28
> **Zugzwang said:**
> As mainerror stated, there is documentation available in the Wiki. An example is the following page: [http://sourceforge.net/apps/trac/aria2/wiki/ArchOverview](http://sourceforge.net/apps/trac/aria2/wiki/ArchOverview) - the architectural overview is a very important document as it tells you something about the overall design of the piece of software. After studying it, whenever you want to modify something, you should be able to identify the parts of the software you will need to touch in order to do so.

For finding out about "xml-rpc", use the respective wikipedia article: [http://en.wikipedia.org/wiki/XMLRPC](http://en.wikipedia.org/wiki/XMLRPC)

Note that many developers do not document class methods if their correct usage is obvious from the context for someone who (1) read the architectural overview and (2) has knowledge of the libraries used. Perhaps this is the case here?

EDIT: Also, the XML-RPC interface [http://aria2.sourceforge.net/aria2c.1.html#_xml_rpc_interface](http://aria2.sourceforge.net/aria2c.1.html#_xml_rpc_interface) seems to be *extremely well* documented. If you don't want to modify the source code for "aria2", there seems to be no necessity to read it.
thank you very much 
I have other questions about developing excuse me
for example if i want to create a button for resume how can i use aria2c api for resume.
how without reading the aria2c code i can recognize  api of aria2c that do resuming download?:roll:please give me an example code about it.
i want to use QT for gui developing.
thanks:P

---

### Post by mainerror on 2010-10-28
> **tah_206207 said:**
> thank you very much 
I have other questions about developing excuse me
for example if i want to create a button for resume how can i use aria2c api for resume.
how without reading the aria2c code i can recognize  api of aria2c that do resuming download?:roll:please give me an example code about it.
i want to use QT for gui developing.
thanks:P

Maybe the API provides a button already trimmed to do just that. I don't really know but I doubt it.

You can't really expect that an API will solve all your problems. You'll most-likely have to learn how to handle click events on your button but again I have no idea about the aria2 API.

---

### Post by tah_206207 on 2010-10-28
> **mainerror said:**
> Maybe the API provides a button already trimmed to do just that. I don't really know but I doubt it.

You can't really expect that an API will solve all your problems. You'll most-likely have to learn how to handle click events on your button but again I have no idea about the aria2 API.
I use click event in this button and when this button clicked i use aria2c api for do resume is this correct?whats's your idea for do this work?

---

### Post by mainerror on 2010-10-28
Sorry can't tell. I'm not familiar with that API.

But looking at the documentation I assume *aria2.unpause gid* is what you are looking for.

Keep in mind tho that I'm not familiar with aria2 it's just a general hint.

---

### Post by tah_206207 on 2010-10-28
how can i relation with aria2c options in my gui program for example i want to use resume aria2c option to create a button resume. how can i use resume option? is there c++ object or function for resume option or any other idea?
what's your idea for doing this?

---

### Post by nvteighen on 2010-10-29
> **tah_206207 said:**
> how can i relation with aria2c options in my gui program for example i want to use resume aria2c option to create a button resume. how can i use resume option? is there c++ object or function for resume option or any other idea?
what's your idea for doing this?

First, do you know how Qt works? Usually, GUI toolkits work in a signal/callback fashion so that for some event that fires up a certain signal, some callback function is performed. But none of this is part of C++: C++ is a programming language aimed for general programming, so its basic data structures and functions are general ones, not the GUI-specific ones you get from a specific library like Qt.

So, without knowing anything about that API (but well, it seems to be extremely well documented), what you have to do is to think how to connect your GUI with the API using Qt's facilities as your "link". I guess all you need is to correctly code the GUI and then set a callback to that particular resume function.

---

### Post by tah_206207 on 2010-10-29
> **nvteighen said:**
> First, do you know how Qt works? Usually, GUI toolkits work in a signal/callback fashion so that for some event that fires up a certain signal, some callback function is performed. But none of this is part of C++: C++ is a programming language aimed for general programming, so its basic data structures and functions are general ones, not the GUI-specific ones you get from a specific library like Qt.

So, without knowing anything about that API (but well, it seems to be extremely well documented), what you have to do is to think how to connect your GUI with the API using Qt's facilities as your "link". I guess all you need is to correctly code the GUI and then set a callback to that particular resume function.
Is this approach is correct?
I want to use xml-rpc in my gui app for doing somethings like for resuming button i use [B]aria2.unpause xml-rpc function.
[B]but for other purpose like create new queue i don't know which function i can use!
can you convince me?
[/B][/B]

---

### Post by mainerror on 2010-10-29
> **tah_206207 said:**
> Is this approach is correct?
I want to use xml-rpc in my gui app for doing somethings like for resuming button i use [B]aria2.unpause xml-rpc function.
[B]but for other purpose like create new queue i don't know which function i can use!
can you convince me?
[/B][/B]

I don't know if we can convince you to do anything but we can only hope you take our feedback and suggestions which would be learn to program from the beginning. In other words learn the basics and then move on to more complicated topics.

I'm sure that no one ran before he started to walk.

---

### Post by tah_206207 on 2010-10-29
> **mainerror said:**
> I don't know if we can convince you to do anything but we can only hope you take our feedback and suggestions which would be learn to program from the beginning. In other words learn the basics and then move on to more complicated topics.

I'm sure that no one ran before he started to walk.
I don't know how can i walk before ran! but i know that i can do

---

### Post by mainerror on 2010-10-29
> **tah_206207 said:**
> I don't know how can i walk before ran! but i know that i can do

I'm just trying to tell you that it appears as if you are trying to run but you don't know how to walk. That isn't going work.

You have to learn the basics of all involved technologies you want to use to really get something solid done.

---

