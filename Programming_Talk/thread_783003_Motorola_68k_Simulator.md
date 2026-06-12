---
title: "Motorola 68k Simulator"
date: 2008-05-05
forum: Programming Talk
---

### Post by Aikon- on 2008-05-05
Hi everyone, I'm going to be helping someone along with a project they have for school. It is written in assembly for a Motorola 68k series processor. Unfortunately, I don't have access to any development boards.

Does anyone know of a good 68k simulator that runs on Linux so that I can test-run my assembly?

Thanks in advance,
-Aikon

---

### Post by Zugzwang on 2008-05-05
Sorry, I've never used one but please keep in mind that these type of software often runs perfectly within wine. Just wanted to mention that. :popcorn:

---

### Post by Eil on 2008-05-05
If you're good with C, you might be able to grab the 68k emulation core from a project like MAME and then wrap a simulator front-end around it. The problem is that if the assembly program is written with a particular development board in mind, there's no way you're going to get it working properly on a simulator or emulator without having detailed specs of the board.

---

