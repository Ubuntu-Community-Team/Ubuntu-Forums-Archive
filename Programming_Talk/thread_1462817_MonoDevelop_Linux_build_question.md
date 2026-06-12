---
title: "MonoDevelop Linux build question"
date: 2010-04-26
forum: Programming Talk
---

### Post by titoki on 2010-04-26
Build problems. I have 10.09 installed I have just installed MonoDevelop and written a very short programme that runs as expected.  However when I build it, the output is an .exe (DOS/Windows)!  What I want is a Linux executable - but cant work out how to build this, any suggestions.  Thanks.

I am a beginner programmer, and hopefully this is not a dumb question.

---

### Post by dwhitney67 on 2010-04-26
It's been a while since I have tinkered with C# under Linux.  When building/running programs, I performed the following steps from the command line:
```

gmcs MyFile.cs

mono MyFile.exe

```
Make sure that your MonoDevelop is doing something similar.  Don't let the .exe extension worry you.

---

### Post by phrostbyte on 2010-04-26
.exe is a meaningless extension, you can remove it if you like and Mono will execute it just fine.

---

### Post by titoki on 2010-04-27
> **dwhitney67 said:**
> It's been a while since I have tinkered with C# under Linux.  When building/running programs, I performed the following steps from the command line:
```

gmcs MyFile.cs

mono MyFile.exe

```
Make sure that your MonoDevelop is doing something similar.  Don't let the .exe extension worry you.
Thanks for those replies.  I think I am starting to understand the process here.

When I build my project in MonoDevelop, gmcs is used and the .exe file is produced.  However there is no sign of the Mono command.

When I manually use the Mono command with the .exe file my application start as normal.  

So progress, but I still do not have a Linux executable - any ideas, or is this part of building 'Packages'?

---

### Post by phrostbyte on 2010-04-27
It is a native Mono executable (with EMCA CIL in it). Don't let the .exe extension fool you. It's only there for compatibility with Windows. 

The idea is to make it (sometimes) possible to run the same executable on Windows and Linux, since both .NET and Mono execute the same machine language.

---

