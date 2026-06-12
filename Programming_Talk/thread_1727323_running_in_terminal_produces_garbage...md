---
title: "running in terminal produces garbage.."
date: 2011-04-12
forum: Programming Talk
---

### Post by jebsector on 2011-04-12
I'm trying to debug a c++ app i'm working on, but when i just ran it in the terminal it produces a bunch of garbage while its running.  i don't know what output it is even producing.  it just takes a file and parses it right now.

This is some of what i'm talking about:

[PHP]
               &#65533;q4 s4Ps4&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;8s4Ps4&#65533;q4
                                                                    `s4&#65533;t4&#65533;u4&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;u4&#65533;u4`s4\s*\'.*\'\s*A&#65533;$&#65533;&#65533;`&#65533;&#65533;&#65533;&#65533;Px4&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;`x4&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; [/PHP]

---

### Post by dwhitney67 on 2011-04-12
You will need to show your source code before anyone can tell you why there is an issue... or if you want, we can play a guessing game.

For now, here's my first guess... you are outputting to standard out the contents of a binary file.

---

### Post by GeneralZod on 2011-04-12
Ooh! Ooh! I guess that you are printing a (C-style) string that is not null-terminated!

---

### Post by jebsector on 2011-04-12
ok apparently all the garbage is coming from the following line:

cout << map->output() << endl;

and in the method output() i forgot to return the string..  :-(

---

