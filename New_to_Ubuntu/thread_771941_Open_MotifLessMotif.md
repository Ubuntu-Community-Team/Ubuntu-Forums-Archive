---
title: "Open Motif/LessMotif"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by amgc5 on 2008-04-28
I am trying to get a specific package installed for which I need to install several s/w packages. For instance, automake, autoconf, lex, bison, openmotif (or lesstiff), ImageMagick, etc. 

I am not sure if these are available for Ubuntu 8.04. Will the ones for the previous ubuntu versions compatible?

---

### Post by Michael.Godawski on 2008-04-28
Which specific package do you want to install? Did you checked if it is available in the Synaptic Package Manager?

---

### Post by amgc5 on 2008-04-28
I am trying to get PSC_DX installed. PSC_DX is a visual programming and application development environment for multidimensional data manipulation and visualization.  It is a derivative of the OpenDX software package, which itself was originally developed by IBM as the proprietary Data Explorer (DX) environment.

I quote: "PSC_DX is a very large software package that includes extensions and bug fixes for OpenDX. We typically build and run it on Linux (Red Hat or Fedora), and we have also built it for Windows using cygwin. However, hardware rendering will not be available with cygwin. In principle it can be compiled and installed on many other UNIX systems but extra tools may need to be compiled and installed prior to the PSC_DX compilation and  installation. As of this release, it can be built on the latest Redhat Linux distributions (RHEL 4.0 and Fedora 4.0) without problems. However, if you encounter compilation errors or choose to run another distro, you might need the following software packages:
    * openmotif (or lesstiff), 
    * ImageMagick,
    * autoconf-2.59
    * automake-1.8.4
    * bison-1.875
    * flex-2.5.4a
    * libtool-1.5.6"

I did try the synaptic manager and alt-get to install softwares, but even after i do so, I continue to get errors. ALso, I was unable to find installation files for OpenMotif.

---

### Post by mister_pink on 2008-04-28
All you need to do is:
```
sudo apt-get install dx
```
Edit: To install open dx that is, sorry just reread your post.
Try
```
sudo apt-get build-dep dx
```
to get things needed to compile them.

---

