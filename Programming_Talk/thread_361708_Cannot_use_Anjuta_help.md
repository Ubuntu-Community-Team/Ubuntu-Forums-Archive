---
title: "Cannot use Anjuta help"
date: 2007-02-14
forum: Programming Talk
---

### Post by billdotson on 2007-02-14
When I try to use anjuta help I get the following screen (attached)

Also when I compile source code it just amkes an object .o file where the source code file is and then I don't know what to do after that (do I need to link it? how?)

thanks

---

### Post by Wybiral on 2007-02-14
If the ".o" is actually an object file, try simply using "g++ hello.o" from the command line.

g++ will do the linking for you.

If that doesn't work... Maybe it's actually an executable (extensions mean nothing in linux) so try to execute it "./hello.o"

(assuming this is the same ".o" you mentioned in a previous post.

---

