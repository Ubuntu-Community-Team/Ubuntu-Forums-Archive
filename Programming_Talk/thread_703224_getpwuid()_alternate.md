---
title: "getpwuid() alternate?"
date: 2008-02-21
forum: Programming Talk
---

### Post by tinkertim on 2008-02-21
Hello to all, 

I'm acquiring memory leaks (and a bit of noise from valgrind) any time I use getpwuid(), (re-entrant or non re-entrant version, the re-entrant version is a bit noisier).

To see what I mean, just run 'id' (from coreutils) through valgrind, it uses the non reentrant version of getpwuid, the rest of the noise comes from gathering groups.

Is there something better I could be using? Thanks in advance.

---

### Post by lnostdal on 2008-02-21
i don't know if anything better exist

i did some quick tests(#1), and it _seems_ that it doesn't leak "more than once" .. what i mean is that if you in your program call *getpwuid* 10000 times it will leak the same (small) amount as if you had called it 1 time

this seems to make sense when i read this:

[quote=man 3 getpwuid]
The return value may point to static area, and may be overwritten by subsequent calls to getpwent(3), getpwnam(), or getpwuid().
[/quote]

..it is a bit vague maybe

anyway .. in these cases [http://valgrind.org/docs/manual/manual-core.html#manual-core.suppress](http://valgrind.org/docs/manual/manual-core.html#manual-core.suppress) might come in handy

#1: can anyone confirm this with some extensive tests? -- i do not have time for this at the moment

---

### Post by tinkertim on 2008-02-21
Your correct, it does not leak more than once and can be suppressed. The leak itself is small compared to what is actually allocated, which of course depends on the # of entries in /etc/passwd.

I just hate to introduce that into something that doesn't leak and reports no errors :) Bah, all I need is to translate uid to login name, I can get everything else safely with getenv.

Ah well, it won't be too hard to write a simple lightweight replacement function.

---

