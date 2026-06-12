---
title: "Reverse Engineering"
date: 2007-09-18
forum: Programming Talk
---

### Post by Majorix on 2007-09-18
Hi.

I will be studying Software Engineering this year, and oddly enough, I am interested in Reverse Engineering i.e. cracking of software.

Under Windows environment cracking is usually done to remove protection from software etc. Even though maybe I will do that in the future, I am not interested in that in the first place. First I want to make bots for games I play. You know, crack your way into the exe, change some stuff and it will play with your strategy without the need for you to be on the computer. Or you play and let the computer do the calculations, timings, aimings (in an FPS game for example) etc. That would be really nice.

First for Windows:
1. What knowledge do I need? Assembly? Binary?
2. What tools do I need? I had some tool that would convert most exes to binary but I lost it and didn't quite understand the output of it :D

Now for Ubuntu:
1. What knowledge do I need?
2. What tools? Preferably on the repos..
3. What can be cracked under Linux?

---

### Post by Wybiral on 2007-09-18
It's the same for both except most Linux software is open source so there's no point.

Basically you'll need to fully understand the MS exe format and the Linux elf.

You'll need a concrete grasp on assembly, particularly being comfortable with reading code that compilers generate. And you'll need, at least, a disassembler and a hex editor.

Learn the executable formats and how to locate the program entry point and linking information (if it's a dynamic library). Then learn to follow that (along with the semi-intelligible crap that the disassembler spits out) to where ever you need.

There may be other tools that I'm unaware of, and this doesn't apply to non-machine code languages like Java... But there really aren't any decompilers worth messing with. You'll just get crap code that's going to confuse you more then the assembly output. So don't expect to do this in C or C++, you need to be comfortable with assembly.

---

### Post by LaRoza on 2007-09-18
For Assembly: [http://laroza.pbwiki.com/Assembly](http://laroza.pbwiki.com/Assembly)

---

### Post by aks44 on 2007-09-18
Do you realize that even game bots *are* illegal (breach of the end-user license)?

---

### Post by LaRoza on 2007-09-18
> **aks44 said:**
> Do you realize that even game bots *are* illegal (breach of the end-user license)?

Wouldn't that depend on the game?

---

### Post by aks44 on 2007-09-18
> **LaRoza said:**
> Wouldn't that depend on the game?

Even GPL'ed games like PlaneShift don't allow bots. Even though technically you *could* be correct, I'd bet I'm on the safe side. ;)


EDIT: anyway, protection-cracking knowledge is just a small part of what is needed to write aim bots and the like. As far as I'm concerned, asking for how to write bots is the same as asking how to crack software. What next? How to write a virus or a rootkit? :-k

---

### Post by Wybiral on 2007-09-18
Well, a lot of them don't allow bots in the servers... There are probably games that let you write bots for them in single player mode.

---

### Post by PriceChild on 2007-09-18
I'm closing this thread.... If you have to be reverse engineering something, then 9 times out of 10 it'll be breaching the license agreement you entered into by purchasing/downloading it.

---

