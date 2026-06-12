---
title: "DSP in Qdevelop??"
date: 2007-10-24
forum: Programming Talk
---

### Post by drinu21 on 2007-10-24
Hi all, 

I am doing a project at school and Part of it needs some DSP algorithms programming. I was asking if Qdevelop with QT4 is powerfull enough for DSP?? also i need to get data from the serial port. i like QT4 cause of the ease to do the GUI. 

thanks,
Adrian

---

### Post by DMills on 2007-10-24
Does your DSP have any sort of realtime requirements?

In general for anything with RT requirements you want to stay away from any code (in the RT path) which allocates memory or can block. This argues that a lot of the QT (and C++ STL, but that does at least give some performance guarantees or a sort) is not really usable in the DSP thread. 

Now there is nothing at all stopping Qdevelop being used as a development ide and even being used for designing the user interface (and even the processing if it is not RT), but for anything remotely hard RT you either want to be working in very careful C++ or straight C IMHO.

For non RT things like offline image processing there is no reason not to do it in whatever you like. 

Regards, Dan.

---

### Post by drinu21 on 2007-10-25
thanks DMILLS, also has anyone used the MATLAB c++ classes in linux??

---

### Post by DMills on 2007-10-25
Not in Linux (we wrote our own custom RT kernel), and not c++, but I have worked on a project that used RTW for code generation together with vast amounts of C-MEX and then used Simulink to build the system.

It ran on an MPC555 (Automotive qualified power pc), and I still have the scars from the license server.

Regards, Dan.

---

