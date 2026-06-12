---
title: "System.Drawing missing in MonoDevelop but present in the documentation?"
date: 2009-08-11
forum: Programming Talk
---

### Post by Jimleko211 on 2009-08-11
I'm trying to make a thumbnail maker for images, and in order to do that I need to call the System.Drawing and System.Drawing.Imaging namespaces.  According to the internal documentation, they are available.  According to intellisense and my compiling errors, I don't have them.  What can I do to solve this problem?

---

### Post by Habbit on 2009-08-11
It does not suffice to say [FONT="monospaced"]using System.Drawing;[/FONT] from your code: the System.Drawing namespace is in an assembly different from corlib, so you must instruct the compiler to import it with the "-r" (Reference external assembly) option, or adding it to the "References" section of your project properties in the IDE you are using. If you have ever programmed in Java, this is akin to "importing" an external JAR file.

---

### Post by Jimleko211 on 2009-08-11
> **Habbit said:**
> It does not suffice to say [FONT=monospaced]using System.Drawing;[/FONT] from your code: the System.Drawing namespace is in an assembly different from corlib, so you must instruct the compiler to import it with the "-r" (Reference external assembly) option, or adding it to the "References" section of your project properties in the IDE you are using. If you have ever programmed in Java, this is akin to "importing" an external JAR file.
I added the reference "mscorlib" in monodevelop, and it's still giving me an error.

---

### Post by Habbit on 2009-08-11
> **Jimleko211 said:**
> I added the reference "mscorlib" in monodevelop, and it's still giving me an error.
If you read my message, I mentioned an assembly **different** from the core library. In particular, you want **System.Drawing.dll**

---

### Post by Jimleko211 on 2009-08-11
> **Habbit said:**
> If you read my message, I mentioned an assembly **different** from the core library. In particular, you want **System.Drawing.dll**
Oh, I'm sorry!  I misread it.  Thank you so much ^_^

---

