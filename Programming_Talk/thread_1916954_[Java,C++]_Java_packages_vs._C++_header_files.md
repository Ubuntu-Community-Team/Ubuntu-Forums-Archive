---
title: "[Java,C++] Java packages vs. C++ header files"
date: 2012-01-29
forum: Programming Talk
---

### Post by Dhiraj Thakur(Invincible) on 2012-01-29
Hi people..
I wanted to ask a question about c++ and java...
Although i know c++ ... i m not that familiar with java...

So the question is " What is the difference between C++ header files and Java Packages?"

I searched on the net but only got vague answers...

---

### Post by CptPicard on 2012-01-29
They're two different things. Header files contain definitions for the compiler to refer to during compilation so that it knows what kind of stuff will be linked into the executable later on.

Java's packages are a namespace system. C++ has namespaces as well, if you want a C++ analogue, you'd want to take a look at them.

---

### Post by ofnuts on 2012-01-29
> **CptPicard said:**
> They're two different things. Header files contain definitions for the compiler to refer to during compilation so that it knows what kind of stuff will be linked into the executable later on.

Java's packages are a namespace system. C++ has namespaces as well, if you want a C++ analogue, you'd want to take a look at them.

The Java equivalent to C++ header files is the "interface" definition.

---

### Post by CptPicard on 2012-01-30
> **ofnuts said:**
> The Java equivalent to C++ header files is the "interface" definition.

Yeah, that too, in a sense.

---

### Post by muteXe on 2012-01-30
> **ofnuts said:**
> The Java equivalent to C++ header files is the "interface" definition.

I disagree. But a namespace anology is a good one.

---

### Post by doobrie on 2012-01-30
> **ofnuts said:**
> The Java equivalent to C++ header files is the "interface" definition.

I don't really agree with that.  An interface in Java is meant to define the contract that a class is to provide.  

A C++ header file defines a class and allows callers to know what the classes definition is.  An interface doesn't define what a class is.

A C++ namespace and a Java package are more abstract containers for classes

---

### Post by ofnuts on 2012-01-30
> **doobrie said:**
> I don't really agree with that.  An interface in Java is meant to define the contract that a class is to provide.  

A C++ header file defines a class and allows callers to know what the classes definition is.  An interface doesn't define what a class is.

A C++ namespace and a Java package are more abstract containers for classes

I didn't says identical but "equivalent". The interface defines what methods you can call, and so does the C++ header  (and I've seen commercial packages where the C++ header doesn't tell you anything else). What the class is is not relevant anyway, what is important is what it looks like, ie, what methods you can call or what attributes you can access.

Besides, in big Java developments, it's not uncommon to define interfaces just for the purpose of avoiding a recompile avalanche. You avoid direct class dependencies across projects by having "transverse" classes represented by interfaces in a specific project  (there is only one class implementing the interface). You can then edit the class body without recompiling the whole workspace. This gets pretty close to how C++ headers are used...

---

### Post by doobrie on 2012-01-30
> **ofnuts said:**
> I didn't says identical but "equivalent". The interface defines what methods you can call, and so does the C++ header  (and I've seen commercial packages where the C++ header doesn't tell you anything else). What the class is is not relevant anyway, what is important is what it looks like, ie, what methods you can call or what attributes you can access.

Besides, in big Java developments, it's not uncommon to define interfaces just for the purpose of avoiding a recompile avalanche. You avoid direct class dependencies across projects by having "transverse" classes represented by interfaces in a specific project  (there is only one class implementing the interface). You can then edit the class body without recompiling the whole workspace. This gets pretty close to how C++ headers are used...

A Java class though may have more methods than an interface has, so there isn't a 1:1 mapping between methods in an interface and in a class.  A class may even implement more than one interface.  In C++, the header usuall have a direct 1:1 relationship with the class,

A Java interface does not define what methods you can call.  It define a contract that the class must implement.  This is not the same as the methods that a developer can call.

A Java interface does not define properties and therefore can be bear little (or no resemblance) to the methods and attributes that a developer can call.

A C++ header is the opposite of this.  It does define exactly what a developer can (and can't) do with a class.

---

### Post by muteXe on 2012-01-30
+1 doobs.

---

