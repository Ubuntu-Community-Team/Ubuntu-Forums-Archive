---
title: "MonoDevelop Quick Question"
date: 2007-10-08
forum: Programming Talk
---

### Post by DaveTheAve on 2007-10-08
If I was to develop an application in MonoDevelop and compile it; does the computer the application was to run on REQUIRE mono to be installed?

---

### Post by ryno519 on 2007-10-08
Yes.

---

### Post by emperon on 2007-10-08
Yes but not compulsory.

Firstly most linux distro and windows boxes can run mono applications out of box.
2nd, you can use mkbundle2 tool of mono to statically link the mono library this way your application will become independent from mono (at the cost of losing cross platformity)

---

