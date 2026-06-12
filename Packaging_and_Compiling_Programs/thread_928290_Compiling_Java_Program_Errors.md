---
title: "Compiling Java Program Errors"
date: 2008-09-23
forum: Packaging and Compiling Programs
---

### Post by coreyxjessica on 2008-09-23
I'm using the acm library and when I type  javac -classpath acm.jar Area.java in the correct path, I get this error: 
1. WARNING in Area.java (at line 10)
	public class Area extends ConsoleProgram {
	             ^^^^
The serializable class Area does not declare a static final serialVersionUID field of type long
----------
Any ideas?

---

### Post by coreyxjessica on 2008-09-23
Anything?

---

### Post by coreyxjessica on 2008-09-23
Anything at all?

---

### Post by qforce on 2008-09-24
The class ConsoleProgram implements the Serializable interface. Since the Area class inherits from ConsoleProgram, it has the Serializable interface, too. This means you have to add a special long field to its class definition, a so-called serialVersion UID.

[http://en.wikipedia.org/wiki/Serialization#Java]("http://en.wikipedia.org/wiki/Serialization#Java")

---

### Post by coreyxjessica on 2008-10-20
> **qforce said:**
> The class ConsoleProgram implements the Serializable interface. Since the Area class inherits from ConsoleProgram, it has the Serializable interface, too. This means you have to add a special long field to its class definition, a so-called serialVersion UID.

[http://en.wikipedia.org/wiki/Serialization#Java]("http://en.wikipedia.org/wiki/Serialization#Java")

How come I don't need to do that in Windows or OS X? Both of them compile fine without adding that.

---

### Post by qforce on 2008-10-21
> **coreyxjessica said:**
> How come I don't need to do that in Windows or OS X? Both of them compile fine without adding that.

Could be anything. Perhaps the Java compiler on your Linux machine has different default settings. Just a guess though because I never had any issues like that.
Btw, what compiler do you use? GCC? That might explain your problem. In that case I'd recommend the javac compiler.

---

### Post by gekkio on 2008-10-23
If the compiling failed, you probably have some other error because that message is just a warning and it should still compile successfully.

The Java language specification recommends adding a serialVersionUid field but it's not required.
You're probably using some different compiler settings than what you use in Windows/OS X (javac uses -Xlint settings to enable/disable warnings).

Anyway...either fix it or don't, it's nothing to worry about.

---

