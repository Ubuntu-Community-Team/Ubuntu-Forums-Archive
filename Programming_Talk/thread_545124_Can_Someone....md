---
title: "Can Someone...?"
date: 2007-09-07
forum: Programming Talk
---

### Post by Shoot3r101 on 2007-09-07
Well now that I have switched to ubuntu everything has changed. I mean my whole life practically. Why you ask? Because before I got Linux I was a Map Designer for Video Games and the programs I used to re-configure the maps BSP,  signature, and other stuff is for windows. I do however have the source code for these applications I used. The source code is in C# but mono will not open it. If anyone could compile a C# source to a Linux application I would very much appreciate it. 

BTW mono refuse's to open the source code.

---

### Post by cdenley on 2007-09-07
Mono refuses to open the source code? Are you using Monodevelop? Does it give an error message? The mono runtime will only open compiled applications. If the compiled application will not run in mono, it either uses functions which haven't been implemented in mono yet, or it uses Windows native libraries. What error message do you get when you try to run the compiled application?

---

### Post by finer recliner on 2007-09-07
mono is not a text edior. it is used to compile and execute .net applications.

say you wrote a hello world app in C# (lets call the file hello.cs). to compile it with mono you use mono's C# compiler (mcs):
```

$mcs hello.cs

```

this creates a file called hello.exe

now to run the file hello.exe you use mono:
```

$ mono hello.exe
Hello World!

```

---

