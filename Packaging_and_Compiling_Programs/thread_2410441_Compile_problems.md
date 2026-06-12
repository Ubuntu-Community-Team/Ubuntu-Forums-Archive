---
title: "Compile problems"
date: 2019-01-15
forum: Packaging and Compiling Programs
---

### Post by ognif on 2019-01-15
Hello, Imm new to Ubuntu and I tried to compile a library from our customer. 

I got the messages:
error: ‘____stat64’ was not declared in this scope
   ____stat64 statbuf;
error: ‘____stat64’ was not declared in this scope
   ____stat64 statbuf;
error: ‘getcwd’ was not declared in this scope
                         if (NULL != getcwd(chFile, _MAX_PATH))





When compile with make. Maybe I have a problem with missing header files? OR what is the problem here? Wrong gcc? 

Thanks,
Ingo

---

