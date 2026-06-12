---
title: "Mono Hello World"
date: 2010-06-21
forum: Programming Talk
---

### Post by alket on 2010-06-21
I did copy paste this [http://mono-project.com/Mono_Basics#Gtk.23_Hello_World](http://mono-project.com/Mono_Basics#Gtk.23_Hello_World) with MonoDevelop

and I get this error

```
/home/alket/csharp/hello.cs(14,14): Error CS0234: The type or namespace name `Windows' does not exist in the namespace `System'. Are you missing an assembly reference? (CS0234) (hello)
```

Same for GTK
What is wrong ?

---

### Post by PaulM1985 on 2010-06-21
You should be using "Window", not "Windows".

You probably have in your code:
Windows window = new Windows("Hello");
or something like that.  Can you post what you are using?

Paul

---

