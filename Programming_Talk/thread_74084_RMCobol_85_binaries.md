---
title: "RM/Cobol 85 binaries"
date: 2005-10-10
forum: Programming Talk
---

### Post by leonleyva on 2005-10-10
Is there any way to run cobol 85 binaries on ubuntu?..

and if is a way how to do it step by step..

Thanks in advance.

---

### Post by Moonbuzz on 2005-10-19
The same with any software, you either need to compile it on the platform you want it to run on, or have some sort of "Runtime environment" it can use (like Java uses, or an emulator). I haven't had much luck with COBOL compilers for Linux, but I'm in the process of trying some of those. It might that they will allow you to execute COBOL binaries compiled on other platforms, but I seriously doubt it. 

The problem with COBOL is that, although it's standartised, it's not interoperable, meaning there's a big difference between ANSI COBOL (COBOL 85) and ACU-COBOL, VAX-COBOL, Fujitsu COBOL, and those are the most used ones. 

As I mentioned earlier, I'm at a process of testing some COBOL compilers for Linux, maybe I'll have some news for you later on this week.

---

