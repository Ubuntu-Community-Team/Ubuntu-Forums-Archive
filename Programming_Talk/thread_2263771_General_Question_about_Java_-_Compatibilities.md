---
title: "General Question about Java - Compatibilities"
date: 2015-02-03
forum: Programming Talk
---

### Post by flaymond on 2015-02-03
Hello, I'm here just to wanna ask a few of questions.

1. Does Java is really compatible? (especially to Android, Linux, and Windows?)
    -If yes, can you explain how it working?

2. Java is fast?
   -I learn that Java is sitting between compiled and interpreted language. This will give any impact at the speed of execution or fast like C or Python?

3. Does programming GUI with it really helpful?
    - I heard a lot from rumors that Java provide you OOP features that really gonna help you programming GUI, is this correct?

4. Java programming language is hard to learn?
   -Also, from rumors. I heard that Java is 'somehow' hard to pick up and complex. Is there any advantages if I learn C and C++ before Java?

* Additional Question (because the curiosity)

   - If I make program in Linux, then can I export it to Windows as exe also run fine in it? 

Thanks for all of you advice and opinions! :KS:KS:KS

---

### Post by The Cog on 2015-02-03
1:
Java can be compatible between platforms if you're careful. Things like filenames - '/' in linux vs '\\' in windows. Java provides (from memory) File.separator that you can use when manipulating file paths. Opening network ports below 1025 is restricted in linux. I have been able to write stuff on one platform and run it on a different one. 

2:
Java is kind of a mix between compiled and interpreted. Quite often, the runtime will compile busy areas of the program on the fly using optimisations that it learns from the way the interpreted version is performing. It is perhaps a little slower than C but probably a lot faster than python for many things, but it depends what you are doing.

3:
You can program a GUI in almost any language. I don't think java is much different, but it is completely object oriented. You really need to get used to the object oriented way of doing things, which can be difficult if you started with C and python. It is well worth it though.

4:
I don't think java is that hard to learn, or complex. It is very exact in its handling of data types though, which can be both a blessing (you always know exactly what kind of object you are dealing with) and a curse (you have to deal explicitly with type conversions). The exacting declaration of object types makes java rather more "wordy" than other languages. C is a simpler language but can be harder to debug - it just crashes, whereas java generally prints an error message that tells you roughly what's wrong and where in your code the problem lies.

5:
I don't know how to make a .exe from a java program. You generally launch the java runtime java.exe and tell it which java class or jar file to run.

---

### Post by ofnuts on 2015-02-03
> **The Cog said:**
> 1:
Java can be compatible between platforms if you're careful. Things like filenames - '/' in linux vs '\\' in windows. Java provides (from memory) File.separator that you can use when manipulating file paths.

The "/" vs "\" issue is overrated because the Windows API accepts both even if it only uses "\" in its answers. So your app can use "/" everywhere it is not displayed to the user or passed to some program that incorrectly rejects names with "/". Other issues with files are (listed here more or less in order of likelihood to hit you):

[LIST]
[*]case significance, maximum length, and encoding of non-ASCII characters in names 
[*]single root on Linux vs multiple roots on Windows 
[*]lack of creation/birth date in most Linux FS and of the change date in Windows, and minor details in timestamps 
[*]lack of archive flag in Linux and of executable flag in Windows (and generally, a different handling of access rights)
[*]behavior of links (because they can also exist on Windows (true links, hard and soft,  and not .lnk shortcuts, which is another well-kept secret) because the links on Windows do not behave exactly like the Unix ones. 
[*]behavior of open files (then can be renamed/deleted in Linux) 
[*]... and I could be missing a few. 
[/LIST]

---

### Post by slickymaster on 2015-02-03
As all of the OP questions have already been thoroughly and correctly answered by both The Cog and ofnuts, I just want to point out to the OP that Java is always platform independent unless you aren't using any special native libraries. It uses a system independent virtual machine for its compiled code, known as bytecode.

---

### Post by flaymond on 2015-02-03
> It uses a system independent virtual machine for its compiled code, known as bytecode.

 Does that mean JVM? It compiles the code, and run the the code in the intrepreter in Java(VM)?

---

### Post by slickymaster on 2015-02-03
> **InterProg said:**
> Does that mean JVM? It compiles the code, and run the the code in the intrepreter in Java(VM)?
When you run a Java application on your computer, cellphone, or any other Java-enabled platform, you essentially pass Java bytecode to the Java Virtual Machine. The interpreter in the Java Virtual Machine usually starts compiling the entire bytecode at runtime, following the principles of so-called just-in-time compilation.
Since Java applications run in a virtual machine instead of directly on hardware, they can be executed on every device with an implementation of the Java Virtual Machine.

---

### Post by ofnuts on 2015-02-03
> **InterProg said:**
> Does that mean JVM? It compiles the code, and run the the code in the intrepreter in Java(VM)?

It's a bit more complicated than this.


[LIST]
[*]You write Java source code
[*]This code is compiled into machine code for a "virtual java machine" (this is the contents of a .class). This code is often called the "bytecode"
[*]The JVM is usually not implemented as a real processor. To execute this code you run a JVM program, that, in the more trivial implementation, reads the byte code instruction by instruction and implements it by executing the equivalent sequence of instructions for your real processor (some x86 variant, usually). This is the same concept as a the emulator that runs vintage console games in a modern PC.
[*]The problem of the trivial implementation is that it is slow, from memory on average about 20 native instructions for one bytecode instruction.
[*]So real JVMs consider the bytecode as some source code for an x86 program and recompile it to produce native x86 code for a whole sequence bytecode instructions. Tnen you get a 1:1 ratio or even better between native and bytecode instructions. This compilation is done on the fly, for code about to be executed ("Just In Time" or "JIT). Code that isn't executed isn't compiled, and you would be surprised by all the code in applications which is seldom or never used.
[/LIST]

---

### Post by flaymond on 2015-02-04
I got it now! Thanks!

---

