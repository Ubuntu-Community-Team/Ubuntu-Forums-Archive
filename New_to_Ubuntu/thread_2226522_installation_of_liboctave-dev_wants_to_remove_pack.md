---
title: "installation of liboctave-dev wants to remove packages"
date: 2014-05-27
forum: New to Ubuntu
---

### Post by black_knight3 on 2014-05-27
Hello everyone,

A recently installed the latest version (3.8.1) of octave  (ppa:octave/stable) on CAELinux2013 (a custom xubuntu 12.04 distribution) and I would like to install liboctave-dev to install  octave packages. When I try to install, the package manager tells me it  will remove the following :

gmsh libhdf5-openmpi-1.8.4 libmed1

I am afraid that removing them will break things, for instance  everything that uses openmpi. Is this true? Is there a way to install  liboctave-dev that will not break everything?

I'm sorry if this is a basic question, I am new to linux.

Thank you

---

### Post by black_knight3 on 2014-05-28
Could anyone at least tell me why liboctave-dev needs to remove gmsh or openmpi?

---

### Post by slickymaster on 2014-05-28
> **black_knight3 said:**
> Could anyone at least tell me why liboctave-dev needs to remove gmsh or openmpi?

Here's the explanation: [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=684930](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=684930)

> <...snip...>liboctave-dev is not coinstallable with the parallel versions of the HDF5 library, what prevents our users of installing libcotave-dev together with the following packages (at least):

$ apt-cache rdepends libhdf5-openmpi-7
libhdf5-openmpi-7
Reverse Depends:
  python-gmsh
  libjava-gmsh2
  libgmsh2
  gmsh
  getdp
  libfeel++1
  feel++-apps
  code-aster-mpi-engine
  code-aster-engine-dbg
  code-aster-engine
  libxdmf2
  libslepc3.2
  libsiloh5-0
  libpetsc3.2
  meep-openmpi
  libmeep-openmpi6
  libmedimport0
  libmedc1
  libmed1
  libmed-tools
  libhdf5-openmpi-dev
  libhdf5-openmpi-7-dbg
  code-saturne-bin
  libcdi0
  cdo
  libadios-dev<...snip...>


---

### Post by matt_symes on 2014-05-28
Beaten to it :). 

Quick typing slickymaster,

---

### Post by black_knight3 on 2014-05-31
Ok, thanks! From what I understand, the problem has to do with liboctave-dev needing a serial version of libhdf5 while I have a parallel version. Do you know of a way of installing liboctave-dev without uninstalling my parallel version of libhdf5? Perhaps by using a static build of liboctave-dev, or by compiling with the mpi version of libhdf5 instead?

---

