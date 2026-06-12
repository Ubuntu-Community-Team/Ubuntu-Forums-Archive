---
title: "error during opening compiled program"
date: 2011-02-23
forum: Packaging and Compiling Programs
---

### Post by MadnessM on 2011-02-23
hi there I compiled a program and when I executed it I got "bash: .: program.exe: impossible to execute the binary file" what could be the problem?
:confused:


thx

---

### Post by ksprasad on 2011-02-23
Hi,
 
 Look at the permission of that file and make sure it has execute permission.
 Actually how did you compile it and how are you trying to execute it?
 
Regards,
ksprasad

---

### Post by MadnessM on 2011-02-23
I compiled it with GCC and I'm trying to execute it from Terminal

---

### Post by ksprasad on 2011-02-23
compile it using,
$gcc program.c -o temp
 
run it,
$./temp
 
Now is it giving the same error? or already are you doing the same thing?
Also check the permission of temp file generated.
 
Regards,
ksprasad

---

