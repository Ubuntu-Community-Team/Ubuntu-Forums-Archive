---
title: "Running opengl programs"
date: 2012-11-20
forum: Programming Talk
---

### Post by mtrumpet on 2012-11-20
I have Ubuntu 12.10 on my laptop. I use an ssh connection to connect to the Linux lab at my university for a programming class. Currently I have been trying to run an opengl program I am working on with a group on my laptop. I am able to access and modify all the files and compile it successfully. All terminal based programs work fine. However when I try to run our current opengl program, skeet, I get the following error: X Error of failed request: BadAlloc (insufficient resoruces for operation). It worked fine one 12.04, but quit working when I upgraded to 12.10. Any suggestions?

---

### Post by Zugzwang on 2012-11-21
First of all, try to see if other opengl programs are running after your update. A typical candidate is "glxgears". If that is the case, consider running your program using valgrind/memcheck. Perhaps there your program has an error, but just happened to work the last time (which is easily possible when working with memory).

```

valgrind --tool=memcheck ./yourprogram

```

---

### Post by mtrumpet on 2012-11-24
glxgears works fine. The problem seems to occur when I connect to my school's network for the linuxlab using and ssh connection and try running my program

---

### Post by mtrumpet on 2012-11-24
when i do the memory check I get the following
==11437== HEAP SUMMARY:
==11437==     in use at exit: 613,194 bytes in 1,542 blocks
==11437==   total heap usage: 2,146 allocs, 604 frees, 1,110,682 bytes allocated
==11437== 
==11437== LEAK SUMMARY:
==11437==    definitely lost: 16 bytes in 2 blocks
==11437==    indirectly lost: 1,026 bytes in 2 blocks
==11437==      possibly lost: 231,735 bytes in 1 blocks
==11437==    still reachable: 380,417 bytes in 1,537 blocks
==11437==         suppressed: 0 bytes in 0 blocks
==11437== Rerun with --leak-check=full to see details of leaked memory
==11437== 
==11437== For counts of detected and suppressed errors, rerun with: -v
==11437== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 6 from 6)

---

### Post by MG&amp;TL on 2012-11-24
Unless mistaken, you might want to forward X so you can run windowed applications.

```
ssh -X user@domain
```

EDIT: Unless you've already got that. Just read the bit about "working fine on 12.04".

---

### Post by mtrumpet on 2012-11-24
yes I forward X, and I can open up text editor windows such as emacs, the problem is when i try running my program

---

