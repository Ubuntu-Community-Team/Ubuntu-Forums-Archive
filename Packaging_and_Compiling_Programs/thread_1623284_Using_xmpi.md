---
title: "Using xmpi"
date: 2010-11-16
forum: Packaging and Compiling Programs
---

### Post by kunigami on 2010-11-16
Hi,
I'm trying to use xmpi library in ubuntu. In the following link there is an example: [http://www.lam-mpi.org/software/xmpi/lam.php]("http://www.lam-mpi.org/software/xmpi/lam.php")

When I try to compile:

```
mpic++ example.cpp -o example
```

I get this error:

> error: ‘XMPI_Buoy’ was not declared in this scope

I have already installed 'xmpi', 'libxmpi4c2' and 'libxmpi4-dev' packages, as well 'lam4-dev', 'lam-runtime' and 'liblam4'.

Can anyone help me on this?

Thanks,

---

### Post by SevenMachines on 2010-11-16
Perhaps you have more than one version of mpicc++ installed? For example libopenmpi-dev or something. Here I have mpic++ set automatically to the last alternative installed so...

> $ ls /usr/bin/mpic++*
/usr/bin/mpic++  /usr/bin/mpic++.lam  /usr/bin/mpic++.openmpiso actually i'm using the openmpi version by default
> $ ls -l /etc/alternatives/mpic++
/etc/alternatives/mpic++ -> /usr/bin/mpic++.openmpiif i try to compile,
> $ mpic++ example.cpp -o example
example.cpp: In function ‘int main(int, char**)’:
example.cpp:13:24: error: ‘XMPI_Buoy’ was not declared in this scope
but, if i specify that i want to use the lam version
> $ mpic++.lam example.cpp -o example

Success!! You could update the alternative or perhaps its easy to pass the right headers to the openmpi version or something but specifying mpic++.lam certainly works here.

---

