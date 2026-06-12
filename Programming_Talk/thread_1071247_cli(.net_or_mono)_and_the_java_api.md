---
title: "cli(.net or mono) and the java api"
date: 2009-02-16
forum: Programming Talk
---

### Post by zizzdude on 2009-02-16
hey, I'm new to .net/mono, and I want to make a certain library using java/ikvm (best language I know so far), and I was wandering if the cli has access to the java api? or if ikvm can use the api?

thanks.

---

### Post by directhex on 2009-02-16
> **zizzdude said:**
> hey, I'm new to .net/mono, and I want to make a certain library using java/ikvm (best language I know so far), and I was wandering if the cli has access to the java api? or if ikvm can use the api?

thanks.

IKVM includes its own embedded copy of (most of) the JDK's classpath.

Your Java app can be written in the normal way, using "import cli;" to import all the .NET stuff from the host system - e.g. "cli.System.Console.WriteLine" exists as well as System.out.println. Compile with "ikvmc". You can use methods in your java-based asembly inside other languages (like C#) in the normal way.

---

### Post by zizzdude on 2009-02-16
> **directhex said:**
> IKVM includes its own embedded copy of (most of) the JDK's classpath.

Your Java app can be written in the normal way, using "import cli;" to import all the .NET stuff from the host system - e.g. "cli.System.Console.WriteLine" exists as well as System.out.println. Compile with "ikvmc". You can use methods in your java-based asembly inside other languages (like C#) in the normal way.

So I am able to use java.util.ArrayList or the java.awt package for example in my library? and other languages will be compatible in using my library?

I'm correct right? :)

---

### Post by directhex on 2009-02-17
> **zizzdude said:**
> So I am able to use java.util.ArrayList or the java.awt package for example in my library? and other languages will be compatible in using my library?

I'm correct right? :)

IKVM's implementation of AWT is *very* pre-alpha quality. But generally, yes, that's correct

---

