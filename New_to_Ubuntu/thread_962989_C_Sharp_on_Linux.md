---
title: "C Sharp on Linux"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by Haruki-kun on 2008-10-29
I have to switch to Windows when I'm doing programming homework because I don't know if I can make C# work on Ubuntu, specifically Microsoft Visual C# 2008 Express. Is there any way to Emulate Windows or to make C# work on Linux?

---

### Post by randy78 on 2008-10-29
If you don't mind using Mono: [http://www.mono-project.com/CSharp_Compiler](http://www.mono-project.com/CSharp_Compiler)

---

### Post by Haruki-kun on 2008-10-29
> **randy78 said:**
> If you don't mind using Mono: [http://www.mono-project.com/CSharp_Compiler](http://www.mono-project.com/CSharp_Compiler)

Can it open Solutions made by Visual C#, and Vice-versa? If so, then it works for me.

---

### Post by directhex on 2008-10-29
"mono-xbuild" package for building sln/csproj files on the command line. "monodevelop" for an IDE. "mono-gmcs" for just the C# compiler.

---

