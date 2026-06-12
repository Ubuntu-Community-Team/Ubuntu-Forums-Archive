---
title: "C++ - Executing a shell process with read and write availability"
date: 2012-10-25
forum: Programming Talk
---

### Post by TheNavigator on 2012-10-25
Hi there guys. I want to make a simple C++ program that runs another process. Let's say the C++ program is X and the other process is Y.

X runs Y through popen for example. When Y requests input, X puts it there according to some received arguments or whatsoever. When Y outputs something, X records it in a string or so.

I know that running a process and reading its output can be done with pipes, popen and these stuff, but I want simultaneous input and output. I searched for it but I can't figure out a solution.

Any help is appreciated. Thanks.

---

