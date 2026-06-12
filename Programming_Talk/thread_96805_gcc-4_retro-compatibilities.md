---
title: "gcc-4 retro-compatibilities"
date: 2005-11-29
forum: Programming Talk
---

### Post by jobherzt on 2005-11-29
I know it's a recurrent problem, but I didn't find the solution. I try to make a source and a binary package for Ubuntu.
but the compilation of the programm, as with fast every source I tried to compile with gcc-4, don(t work beacause of an "lvalue assignement error". But with gcc-3.3, the compilation work fine, altough he warn that "use bla bla lvalue is deprecated". so it's logical, gcc-3 warned, and gcc-4 refuse. but for respecting Ubuntu policy I must use gcc-4. so I want to know if it exist an issue for that, an option to make gcc-4 compatible with the 3.3 ?

excuse me fr my english, I'm french :D 

thank you !

---

### Post by thumper on 2005-11-30
I'd suggest fixing the code.

---

### Post by jobherzt on 2005-11-30
of course, in this case it's what I'm going to do. I found the problem in the source. But the programm is relativ small, sou it's not so difficult, but it will not alwas be so, so I wanted to know if there is a trick to fix it more fastly.
thanks

---

### Post by thumper on 2005-11-30
I don't believe there are any "magic" porting tools.  This is one of the problems when moving to a more standards compliant compiler.

Just be thankful you are not moving from VC6 to VC7.1 or gcc as there is more pain there.

---

### Post by jobherzt on 2005-11-30
lol :p :p :p

---

