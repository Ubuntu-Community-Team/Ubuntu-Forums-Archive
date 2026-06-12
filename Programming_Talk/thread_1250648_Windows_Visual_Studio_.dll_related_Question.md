---
title: "Windows Visual Studio .dll related Question"
date: 2009-08-26
forum: Programming Talk
---

### Post by SNYP40A1 on 2009-08-26
I am not sure if this is the best place to ask this question, but I know there are a lot of skilled programmers here who might have an answer.  If there's a better place to ask this, let me know.

I am trying to compile a class into a .dll, but the class inherits from another class.  So say I have a base class called animal that I compile into animal.lib.  I then want to create a subclass called Dog which inherits from animal.  Is there a way to do this so that at runtime, only dog.dll is needed and not dog.dll and animal.lib?  In other words, I compile dog.dll from the dog and animal sources instead of compiling a smaller dog.dll which is required to link with animal.lib at runtime.  Anyone know how to do that?

---

