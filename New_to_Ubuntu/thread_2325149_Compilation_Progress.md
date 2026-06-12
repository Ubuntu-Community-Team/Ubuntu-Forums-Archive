---
title: "Compilation Progress"
date: 2016-05-19
forum: New to Ubuntu
---

### Post by Lector41 on 2016-05-19
Hello all,

I am pretty new to Ubuntu and Unix type environments so please bear with me if I have some trouble articulating my problem.  I have to turn on some extra options in the kernel.  So far everything has worked fine but I need to compile and install it on a number of different machines and they all have very different processing speeds.  I just wanted to know if there is any way to see the progress of the compiler (like a 1-100% scale type deal).  I know compilation will take a while but it would just help me plan around my other work if I knew how much time it would take.  Thank you for your help in advance!

Clyde

---

### Post by oldrocker99 on 2016-05-20
Generally, there's no progress notification visible with gcc or g++. Various PCs do compile at different speeds; I compiled wine one time on a laptop and it took well over an hour. Compiling it on my desktop took <20 minutes. 

Sorry to be the bearer of bad news. If I'm right.

---

### Post by Lector41 on 2016-05-20
That seems to be the general consensus around here as well.  Thank you for the reply!

---

### Post by cariboo on 2016-05-20
You could do the compile for the different systems on your fastest system, they copy the resulting kernel debs to the various systems.

---

### Post by SeijiSensei on 2016-05-21
> **cariboo said:**
> You could do the compile for the different systems on your fastest system, they copy the resulting kernel debs to the various systems.
Assuming that the other systems share the same architecture.  Otherwise you'll need to compile on a 32-bit system for other 32-bit machines, and on a 64-bit system for 64-bit machines.

---

