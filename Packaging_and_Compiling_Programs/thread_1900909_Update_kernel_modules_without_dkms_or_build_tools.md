---
title: "Update kernel modules without dkms or build tools?"
date: 2011-12-27
forum: Packaging and Compiling Programs
---

### Post by djsephiroth on 2011-12-27
I have built a package that installs a kernel module (among other things). The package (at least the module) needs to be rebuilt for each new kernel. However, the target systems need to be lean, with no build tools or dkms; what are my options? 

I'm thinking about a vm with build tools + a script that rebuilds the package when a new kernel is released, then sends it to a local apt repo. Am I going down the wrong path?

---

