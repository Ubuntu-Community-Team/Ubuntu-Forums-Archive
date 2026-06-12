---
title: "Multiarch and 32-bit binary only programs"
date: 2011-09-17
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by tghe-retford on 2011-09-17
I noted a problem reinstalling Oneiric, with the changes due to multiarch support, programs which are released as a binary only file (thinks Kega Fusion) as opposed to a debian package are going to be a pain to get working, and getlibs can't bail you out.

Talking of Kega Fusion, the changes made now mean that on a 64-bit system (it's only released as 32-bit binary), the program will either fail to run or produce a segmentation fault. In the past ia32-libs was all that was needed and it would run without any further intervention.

Is there any way find out what i386 packages are needed for programs which are released purely as a binary only file, as per getlibs before, so that they can run under Oneiric?

Thanks in advance

---

