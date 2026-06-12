---
title: "Mono question"
date: 2012-03-24
forum: Programming Talk
---

### Post by Drenriza on 2012-03-24
Hi guys.
 
I have on and off worked on a C# project (hobby). And was wondering what it would take to make it work on Ubuntu.
 
From what i know about Mono, it examines the C# code and translate it to C for the Linux OS. My question is as follows. My project is a Winforms project, will the gui of the winforms project be translated by mono to something Ubuntu can understand? Or do i need to do something to make it run in gtk+ (i think its called).
 
Thanks on advance.
Kind regards.

---

### Post by ysangkok on 2012-03-24
> **Drenriza said:**
> Hi guys.
 
I have on and off worked on a C# project (hobby). And was wondering what it would take to make it work on Ubuntu.
 
From what i know about Mono, it examines the C# code and translate it to C for the Linux OS. My question is as follows. My project is a Winforms project, will the gui of the winforms project be translated by mono to something Ubuntu can understand? Or do i need to do something to make it run in gtk+ (i think its called).
 
Thanks on advance.
Kind regards.

No, it does not translate anything to C code. Mono has it's own VM just like .NET.

Winforms isn't supported as well as GTK# in Mono, but there is some support. You could try executing your program and see which exceptions you get.

GTK# is a completely different different API and you'd have to redo your whole UI layer. If it is a hobby project that shouldn't be too hard.

---

