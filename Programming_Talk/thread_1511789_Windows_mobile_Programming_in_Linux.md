---
title: "Windows mobile Programming in Linux?"
date: 2010-06-17
forum: Programming Talk
---

### Post by hakermania on 2010-06-17
Hello all, I am a bit interested in windows mobile programming. You can program in vb C# and C++ (I am interested in C++). I am using QtCreator and 7zip supports .cab compression (Windows mobile does support only .CAB packages.)...So, I know C++ and I can compress my program to .cab...... Do I need anything else?

---

### Post by nvteighen on 2010-06-17
> **hakermania said:**
> Hello all, I am a bit interested in windows mobile programming. You can program in vb C# and C++ (I am interested in C++). I am using QtCreator and 7zip supports .cab compression (Windows mobile does support only .CAB packages.)...So, I know C++ and I can compress my program to .cab...... Do I need anything else?

You'll also need whatever runtime WinMobile uses and compile your program to PE, not ELF Linux executables. If you're able to create a development environment in GNU/Linux to do this, there shouldn't be any problem, but I doubt there is.

---

