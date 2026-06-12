---
title: "Dual OS/ Mulitithreaded programming/Compiling"
date: 2009-01-23
forum: Programming Talk
---

### Post by AnthonyNYU on 2009-01-23
Will having two OS installed on my computer change the behavour of serial or mulithreaded programming compilation (with C for instance). I want to make sure that my code stays "close to the machine", I do not want to have to go through virtual or emmulation layers. I will be using OpenMP to push code though the CPU (quad core), and CUDA to push through the GPU.

---

### Post by monkeyking on 2009-01-23
I don't quite understand what you want.
Having two os installed wont matter anything as long as you  boot up native.
But are you talking about runing one os in a virtual box?

Are your os both unix or windows also?

As far as I know, only boost threads gives you a uniform method of cross system threading.
Otherwise you should use the intel threading block
[http://www.intel.com/cd/software/products/asmo-na/eng/294797.htm](http://www.intel.com/cd/software/products/asmo-na/eng/294797.htm)
These offer a templated approach to multiprogramming.
But are as such not free.

Have you ever done thread programming before?

---

### Post by jdrodrig on 2009-04-15
Something to have in mind; is that if you have one of the two OS as virtual machine, you need to make sure your virtualization solution (eg virtualbox, vmware player, workstation) supports guest with dual processors. 

Are you thinking how two threads in the guest OS would map to the threads running in the host?

---

### Post by dribeas on 2009-04-16
> **monkeyking said:**
> 
As far as I know, only boost threads gives you a uniform method of cross system threading.
Otherwise you should use the intel threading block
[http://www.intel.com/cd/software/products/asmo-na/eng/294797.htm](http://www.intel.com/cd/software/products/asmo-na/eng/294797.htm)
These offer a templated approach to multiprogramming.
But are as such not free.


There are other libraries: ACE, PoCo, QT, probably (I have never used it) gtkmm, or wxWidgets. Most multiplatform frameworks have their own wrapper around native threads. Oh, and of course, C++0x will have threads (very close to the current boost implementation)

---

