---
title: "c error"
date: 2010-03-11
forum: Programming Talk
---

### Post by newport_j on 2010-03-11
I received the following error in compiling a c program.

:101: error: expected expression before ‘int’

The module is called by this lie:

VRT_RAY2_FIRST_GPU(int IRAY, int MINRAY, int MAXRAY, double TIMv,
                       double *ZRAYu, double *TRAYu, double *PCOSu, double PSINu,
                       int *NSRFU, int *NBTMu, int *NUPRu, int *NLWRu); 
 
What is the error? I am a c newbie and I do not see it.

Newport_j

---

### Post by Zugzwang on 2010-03-11
If you call a method, you do not supply types for each argument, this is only done when declaring a method.

---

### Post by newport_j on 2010-03-11
So do I correct it by dropping the types of each argument in the calling line?
 
Newport_j

---

### Post by CptPicard on 2010-03-11
Could I suggest you quickly read through [K&R]("http://en.wikipedia.org/wiki/The_C_Programming_Language_(book)")? It's concise and will help you a lot in your endeavours...

---

### Post by era86 on 2010-03-11
> **newport_j said:**
> I received the following error in compiling a c program.

:101: error: expected expression before ‘int’

The module is called by this lie:

VRT_RAY2_FIRST_GPU(int IRAY, int MINRAY, int MAXRAY, double TIMv,
                       double *ZRAYu, double *TRAYu, double *PCOSu, double PSINu,
                       int *NSRFU, int *NBTMu, int *NUPRu, int *NLWRu); 
 
What is the error? I am a c newbie and I do not see it.

Newport_j

I believe this will depend on context.  Are you trying to create a new function?  Or are you calling a function?  You're going to want to remove the type declarations if you are calling VRT_RAY2_FIRST().

---

### Post by soltanis on 2010-03-12
This looks like a C function trying to be prototyped. It doesn't show a return type, though; unless it has a return type on the line above it, I would say that that's why.

Check line 100 for a return type, on its own line, without any semicolons.
If there isn't one then that's what needs to get fixed.

---

