---
title: "OpenMPI"
date: 2009-05-17
forum: Programming Talk
---

### Post by fivos on 2009-05-17
Hi everyone, 
I would like to install OpenMPI on my linux ubuntu64bit PC, in order to learn how to use it. I have found in the ubuntu repositories from the synaptic package manager the OpenMPI 1.2.6 version and from the OpenMPI web page ([www.open-mpi.org]("http://www.open-mpi.org")) the most recent version 1.3.2. So I want to ask anyone who has installed and used OpenMPI, or anyone else who thinks that can help: 
-Which version do you suggest me to use/install?
-Can you guide me how to customize OpenMPI? To be more specific, I want to link OpenMPI to my fortran Compiler, Intel Fortran 11.083, so I can use the wrapper. How can I do that? Or how can I build an executable from source with the OpenMPI directives, using makefiles (what libraries do I need to include)?
Since I am a bit new to linux, detailed instructions would be appreciated.
Thanks in advance.

---

### Post by AB000DY on 2009-11-03
> **fivos said:**
> Hi everyone, 
I would like to install OpenMPI on my linux ubuntu64bit PC, in order to learn how to use it. I have found in the ubuntu repositories from the synaptic package manager the OpenMPI 1.2.6 version and from the OpenMPI web page ([www.open-mpi.org]("http://www.open-mpi.org")) the most recent version 1.3.2. So I want to ask anyone who has installed and used OpenMPI, or anyone else who thinks that can help: 
-Which version do you suggest me to use/install?
-Can you guide me how to customize OpenMPI? To be more specific, I want to link OpenMPI to my fortran Compiler, Intel Fortran 11.083, so I can use the wrapper. How can I do that? Or how can I build an executable from source with the OpenMPI directives, using makefiles (what libraries do I need to include)?
Since I am a bit new to linux, detailed instructions would be appreciated.
Thanks in advance.
Iwould Help too !!!
 
Thanks in advance.

---

### Post by nardis_Miles1 on 2009-12-31
I had openmpi-bin installed under jaunty. I'm getting the following installation error under karmic:

Setting up openmpi-bin (1.3.2-3ubuntu1) ...
update-alternatives: error: alternative mpiexec can't be master: it is a slave of mpirun

Has anyone else had a similar problem?

---

### Post by nardis_Miles1 on 2010-01-05
Replying to my own post, this problem vanished when I did a dist-upgrade today. All is well with openmpi.

---

### Post by auriza on 2010-01-05
I use OpenMPI on Ubuntu 9.04 [ ["]http://auriza.site40.net/notes/mpi/openmpi-on-ubuntu-904/]("http://auriza.site40.net/notes/mpi/openmpi-on-ubuntu-904/) ] and I prefer package from Ubuntu repo although the version is older than the latest version. **mpicc** and **mpif90** is just a wrapper, you can show the underlying compile and link configuration by using this command:

[B]mpif90 [-showme:compile|-showme:link]

[/B]And then hopefully you can change the Fortran compiler to your preference.

---

