---
title: "install MPI-- &quot;configure: error: Namespaces are required for the MPI C++ interface&quot;"
date: 2009-10-17
forum: Programming Talk
---

### Post by jaycui on 2009-10-17
Hello:

I want to run mpi program 

I download the mpich2-1.0.4p1.tar.gz. and get an error after: ./configure --prefix=/urs/local/mpich2 
"checking for gcc... gcc
checking whether we are using the GNU C++ compiler... no
checking whether gcc accepts -g... no
checking whether the compiler supports exceptions... no
checking whether the compiler recognizes bool as a built-in type... no
checking whether the compiler implements namespaces... no
configure: error: Namespaces are required for the MPI C++ interface"

Has anyone also got such problem?  What should I do to solve it?:confused:
Thanks!

---

### Post by MadCow108 on 2009-10-17
have you got the build essentials installed?
apt-get install build-essential

---

### Post by jaycui on 2009-10-17
> **MadCow108 said:**
> have you got the build essentials installed?
apt-get install build-essential

Thank you! problem solved.

---

