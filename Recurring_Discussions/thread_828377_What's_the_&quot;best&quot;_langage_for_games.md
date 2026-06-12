---
title: "What's the &quot;best&quot; langage for games ?"
date: 2008-06-13
forum: Recurring Discussions
---

### Post by Stochastics on 2008-06-13
Hi everyone,

Like it's said in the title : What's the "best", if this thing exist, programming langage for game programming ? Or, what's the standard langage use today in the market ?

Stochastics

---

### Post by -grubby on 2008-06-13
I can't really say, but it seems as if most games I see are written in C. I could be wrong

---

### Post by moephan on 2008-06-13
FWIW, I found it super easy to build an asteroids clone using Python and PyGtk.

Cheers, Rick

---

### Post by Phenax on 2008-06-13
Depends what type of game you want to develop.

For a commercial-grade video game that requires heavy graphics/physics/etc. - C/C++
For a hobbyist game you could use C/C++, Python, Ruby, Lua, or pretty much any language out there.

---

### Post by bruce89 on 2008-06-13
> **nathangrubb said:**
> I can't really say, but it seems as if most games I see are written in C. I could be wrong

C++ I'd say, which is a shame.

---

### Post by LaRoza on 2008-06-13
> **Stochastics said:**
> 
Like it's said in the title : What's the "best", if this thing exist, programming langage for game programming ? Or, what's the standard langage use today in the market ?

Stochastics

It depends. The game engines are often written in C or C++, but most game programming is on game engines.

Python, Perl, and Java for example are used in games. Many languages use more than one language, often using a "scripting" language.

---

### Post by descendency on 2008-06-13
As previously stated, most software companies rely on C\C++ for game building. 

It's not necessarily because it's the best, but it's the most common that large portions of their infrastructure is setup for. Changing that would be highly expensive.

---

### Post by pmasiar on 2008-06-13
First, I would recommend **not** considering career in game programming: google for scary stories, game industry is brutal, and burnout rate is huge - but that model is supported by steady inflow of starry-eyed fresh programmers, who think that programming games has to be fun. 

If you want to program games as a hobby, consider either contributing to an existing game (and then your language is fixed), or the most productive tool to write game code - which today is Python, and probably with pygame library. With Python, you can always optimize code later, converting it to C library - but only when and if it is needed, and with fixed API.

Yet another option is to join our project, GameBaker, or the original GameMaker - that's even easier than pygame.

---

### Post by bapoumba on 2008-06-14
Moved to "Recurring Discussions".

---

### Post by raul_ on 2008-06-14
Probably anything Object Oriented. Since java needs to have a virtual machine running, I guess that leaves C++ and python. It's just my guess, and I'm not saying that other languages suck, just that OO programming makes more sense to me, for games.

---

### Post by neoAnderson on 2008-06-14
In my AI class we used C++ to build a game with artificially intelligent agents... one of the prime reasons was that we were using vision (Webcam), and Microsoft offers huge libraries for vision and webcam management - the Windows Platform SDK and a whole lot of stuff... and all that integrated well with C++. Additionally the facts that C++ is object oriented (which facilitates state-driven game programming - one of the most widely followed paradigms in game development), and that it is faster than Java in mathematical calculations... lead me to set my choice as C++.

---

