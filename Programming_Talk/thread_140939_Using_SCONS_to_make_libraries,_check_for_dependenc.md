---
title: "Using SCONS to make libraries, check for dependencies and compile an executable."
date: 2006-03-07
forum: Programming Talk
---

### Post by Sslaxx on 2006-03-07
I'm currently learning more about using the SCONS system for making programs and libraries. What I'd like to do with it is:

[LIST]
[*]Check for dependencies.
[*]Create a static library.
[*]Compile an executable.
[/LIST]

I can get it to to the last two, and I know how to do the first. What I'd *really* like is for one SConstruct file to call another, which does the dependency checking and static library creation, before continuing on to create an executable using that static library. I'm not sure how to go about this.

Advice?

---

