---
title: "Error in compiling vasp 5.3"
date: 2016-06-20
forum: Packaging and Compiling Programs
---

### Post by manish23 on 2016-06-20
While compilation, I am getting the following error:-

VERY BAD NEWS! internal error in subroutine SGRGEN:
 Too many elements      49

Any suggestion on how to rectify this error?

---

### Post by steeldriver on 2016-06-20
Hello and welcome to the forums

That sounds more like a runtime error (possibly from a unit test during building?) than a compilation error

There appears to be a bug report here [http://cms.mpi.univie.ac.at/vasp-forum/viewtopic.php?f=3&t=17048](http://cms.mpi.univie.ac.at/vasp-forum/viewtopic.php?f=3&t=17048)

---

### Post by manish23 on 2016-06-20
Thanks for answering...:)

I went through the bug report. I came to realise that its working perfectly fine for ISYM=0 (tag in INCAR file), but is showing the afore-mentioned error for ISYM=1,2

I wanted to run it using default ISYM=1 tag. Can you please help?

---

### Post by steeldriver on 2016-06-20
Sorry, I don't have any experience with that software - unless someone else on these forums does, you are probably better posting your question on the vasp forum

---

