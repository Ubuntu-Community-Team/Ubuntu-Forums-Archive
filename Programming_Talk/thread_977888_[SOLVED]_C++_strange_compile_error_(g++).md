---
title: "[SOLVED] C++ strange compile error (g++)"
date: 2008-11-10
forum: Programming Talk
---

### Post by Pagh on 2008-11-10
Hi.

When I try to compile a program that i made i get the following compile error:

"test.cpp:52: warning: direct base ‘vector’ inaccessible in ‘vectorCalc’ due to ambiguity"

What does this ambiguity means? I searched Google but couldn't find an answer. 

Hope there is anyone that is able to help.

All the best Kasper Roland Pagh

---

### Post by dribeas on 2008-11-10
> **Pagh said:**
> Hi.

When I try to compile a program that i made i get the following compile error:

"test.cpp:52: warning: direct base ‘vector’ inaccessible in ‘vectorCalc’ due to ambiguity"

What does this ambiguity means? I searched Google but couldn't find an answer. 

Hope there is anyone that is able to help.

All the best Kasper Roland Pagh

A longer error report and source code around the error would really help determining the real error.

---

### Post by Pagh on 2008-11-10
I solved the problem by myself my brain just bugged up for a while ;-D
I think the warning came be course that I had a (lets call it class3) class3 that inherited another class(2) the inherited another class(1).

When I defined class3 I'd let it inherit both class 1 and 2. So  class3 inherited class1 two times. 

However it's solved now so I'm very sorry to have created this rather useless thread.

---

### Post by StOoZ on 2008-11-10
good.
but next time , provide the code , and all the errors you're getting.

---

