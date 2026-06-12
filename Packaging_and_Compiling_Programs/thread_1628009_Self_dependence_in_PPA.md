---
title: "Self dependence in PPA"
date: 2010-11-22
forum: Packaging and Compiling Programs
---

### Post by kvdveer on 2010-11-22
I'm trying to create a PPA, but unfortunately most of my builds fail due to an internal dependency.
My PPA provides a library (libgrace), which provides build dependency for all other packages. 

I'm not allowed to add the PPA as a dependency to itself, which is how I solved this at my local machine. I might be able to solve this using multiple PPA's, but that would complicate installation for users, which I'd rather avoid.

Does anyone know I could fix this?

---

### Post by SevenMachines on 2010-11-22
The ppa build automatically checks for required dependencies inside of the same ppa, i'm guessing the build failure is due to something else

---

### Post by kvdveer on 2010-11-23
Turns out self-dependence "just works", only there is a significant delay between a package being built and the package becoming available for dependencies (several minutes). This, and the fact that builds are performed in parallel, caused dependencies to fail.
Restarting the build after allowing the dependencies to become available solved the problem for me.

---

