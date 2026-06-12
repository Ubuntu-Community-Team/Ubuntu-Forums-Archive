---
title: "Compiling/Swapping Xorg?"
date: 2013-06-25
forum: Programming Talk
---

### Post by KingOfHorses on 2013-06-25
Hello all.  I am able to compile Xorg Server LTS Quantal 1.13.0; however, when I try to replace the pre-packaged Xorg binary with the binary from compilation, on a reboot, things fail to varying degrees.  Failures are not consistent and tend to range from those where I can drop to root to fix the problem to failures where I cannot.  Running ldd and size on the two Xorgs shows they use the same shared libraries, though the sizes of the two binaries are different.

My goal is to have a working, compiled Xorg of my own which can be swapped out for the currently working Xorg so that I can modify it, see what happens, and if things start to break, I can drop down to root to fix the problem by swapping the original Xorg back in.

I am running Ubuntu 12.04 LTS Precise.  Can anyone offer any advice with regards to achieving my goal?

---

### Post by Toz on 2013-06-25
Moved to ***Programming Talk*** subforum.

---

### Post by KingOfHorses on 2013-06-26
Solved.  Installation needed to happen in single user mode.

---

