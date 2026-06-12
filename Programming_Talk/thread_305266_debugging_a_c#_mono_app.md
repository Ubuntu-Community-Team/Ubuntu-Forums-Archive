---
title: "debugging a c# mono app"
date: 2006-11-23
forum: Programming Talk
---

### Post by jordilin on 2006-11-23
I'm learning c# with the mono platform. Now I have a question. How people debug programs in Mono. I haven't seen any debugger. MonoDevelop doesn't ship a debugger yet. In m$ win SharpDevelop and Visual Studio both have debuggers, so you can see what's going on at any moment. How linux guys who program in c# mono debug their applications? is their a way? thanks

---

### Post by jordilin on 2006-11-24
anybody?

---

### Post by engineer on 2006-11-24
i can tell you my method for debugging:

the console output produced by exceptions shows you line numbers.
beside this, i insert console output commands to see the values of my variables. it's no perfect debugger, but in most cases it's enough.

---

