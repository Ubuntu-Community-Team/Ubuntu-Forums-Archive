---
title: "Swing GUI Builder"
date: 2009-12-15
forum: Programming Talk
---

### Post by Majorix on 2009-12-15
I want to use the Swing API for GUI development with languages OTHER THAN Java, and WITHOUT hand-coding the tools.

I tried to accomplish that using Jython under NetBeans, but I didn't get an environment where you can drag&drop buttons, textboxes and so on. I have googled around a bit but didn't really come across something useful.

I could also use JRuby instead of Jython if it is not possible to drag&drop using Jython and it is with JRuby.

I also stumled upon a language called Groovy, which claims to be "An agile dynamic language for the Java Platform". Can you use the NetBeans IDE to develop a GUI for this language automatically?

Thanks!

---

### Post by brendon9x on 2009-12-16
Hi Majorix,

I'm writing something which may be able to help you out (with some minor work), although I would better like to understand what exactly you expect the generated code to look like.  Please email me on brendon//at//mindsilver.com

Regards,
Brendon.

---

### Post by jespdj on 2009-12-16
Yes, Groovy is a scripting language with a Java-like syntax, but without the verbosity of Java. NetBeans has good support for Groovy, but I don't know how well it works with NetBeans' GUI builder.

If you want to build a Swing GUI application with Groovy, then the [Griffon](http://griffon.codehaus.org/) application framework might be interesting.

---

