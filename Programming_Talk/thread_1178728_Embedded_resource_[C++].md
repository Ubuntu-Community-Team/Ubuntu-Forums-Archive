---
title: "Embedded resource [C++]"
date: 2009-06-04
forum: Programming Talk
---

### Post by Freiddie on 2009-06-04
Hello,

I know this might sound strange to other unix programmers, but I have been wondering if there is an equivalent of the so-called "Windows resource scripts" that is cross-platform?

What I intend to do is to have some XML data file that is part of the compiled executable, rather than as a separate file (which might get lost, modified unintentionally, etc.), and is there any easy way to do this? And if this isn't a common practice in unix programming (or that my idea is too awkward), please do say so.

Thanks in advance.

Freiddie

---

### Post by mart_k on 2009-06-05
I don't know anything about resource scripts, but I will try to answer it.

You have an xml-file, which you want to be part of the executable. This means that that file cannot be changed easy after it is compiled (correct me if I am wrong). So it really behaves like a constant char* (which also is stored in the executable, IIRC). So for me, the most obvious solution is to use (write?) a script that converts you xml-file to a C-string (that is easy: you just have to replace chars like " with \" and so) and make sure you can use that string in your program. Then in the program, you can use your string instead of the xml-file.

I must say I don't really see the usefullness of this. If it contains settings, then defines are usually more usefull. In general, this seems like a bit slow solution, because the whole contents of the xml-file is known at compile-time, but you don't use that: you parse the file run-time.

---

### Post by Npl on 2009-06-05
Nope, not possible until you mean embedding it directly in the code like mat_k said.

mat_k: embedded resources ala windows are nice, you can for example bundle string-tables and images in multiple languages. The right language will be automatically chosen. You can even share those resources between processes, eg. icons.
Unlike embedding that stuff directly in code, the additional resources dont take up memory unless used.

And you can modify them (via standards Win32-API), altough thats not a good way to use them IHMO

---

### Post by Freiddie on 2009-06-05
Thanks for answering my questions.

So apparently there isn't any easy way of doing this. I understand that putting an XML file into a string is going to waste a lot of memory (and I only need to access it once).

Oh well, I guess I have to use an external XML file then (for GtkBuilder).

Freiddie

---

