---
title: "source installation"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by raedbenz on 2008-06-09
HI...
i have a package with ".tar.bz2" extension.
i extracted it and it generated at the same path a folder called "arm-2008q1"
inside it there are these folders:[ATTACH]73436[/ATTACH]

what to do to install it ? what are the commands
i tried "./configure" but it didn't work.
tnaks

---

### Post by KingTermite on 2008-06-09
I see lib, header directories, but not a source. Do any of the directories have source files, especially a file named "Makefile"?

If so, go in to that directory from a command line and try "make" to see if you have to build source.

---

