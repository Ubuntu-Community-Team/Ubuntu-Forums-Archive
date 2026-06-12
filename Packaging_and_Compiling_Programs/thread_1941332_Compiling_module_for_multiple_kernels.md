---
title: "Compiling module for multiple kernels"
date: 2012-03-15
forum: Packaging and Compiling Programs
---

### Post by djsephiroth on 2012-03-15
I have a package "foo" that includes a kernel module "whatever.ko". I want to keep the module updated for several machines, but without installing build tools, dkms, etc. (They need to be very lean and generally not messed with.)

I have created a dkms setup to rebuild the module on a server box as needed. From there, I suppose I could send the correct version of "whatever.ko" to each of the other boxen. Would it be best to do this by simply copying it? (I use Puppet, so it seems like this option would be easy to implement.) If I overwrite the "whatever.ko" file, will that break the package "foo" somehow?

How does this sort of thing normally work in Linux? How do the drivers on my desktop box work after kernel updates? Mysteries.

---

