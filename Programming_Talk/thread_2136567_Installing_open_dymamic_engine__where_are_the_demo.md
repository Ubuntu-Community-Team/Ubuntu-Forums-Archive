---
title: "Installing open dymamic engine : where are the demos ?"
date: 2013-04-18
forum: Programming Talk
---

### Post by vincentberenz on 2013-04-18
Hi,

I am new at compiling libraries.
I compiled ODE using the autotools following the instruction of the install file.
(running configure, then make and make install).
Everything seems fine and the library is installed in usr/local/lib.

I would like to run the demo but have no idea where the executable are supposed to be. Looked everywhere for them, without sucess.

Note:
When executing in the ode source folder:
./configure --help
I get the information that the feature --disable-demos can be used when configuring the build. From this I assumed that if you do not use this feature (and I did not), the demos are built.

thx !

---

### Post by vincentberenz on 2013-04-18
oh, turns out that opengl was not installed, which cause configure not to build the demo.

---

