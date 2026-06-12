---
title: "HOWTO set the environment variable"
date: 2006-08-25
forum: Packaging and Compiling Programs
---

### Post by Xiong on 2006-08-25
While i am building a project on F compiler platform, i have trouble in make.The note is as below
:```
make -k all 
Please specify the target machine!
Either use on the make command line:
  make MACHINE=target
or define the environment variable MACHINE by:
  export MACHINE=target
target can be one of:
linux_pgi, linux_pgi_debug
linux_absoft, linux_absoft_debug
linux_lahey, linux_lahey_debug
ibm, ibm_debug
vpp, vpp_debug, vpp5000
hp, hp_debug, sun, sun_debug
epc, epc_debug, cray, cray_debug
linux_intel, linux_intel_debug
```

Where can i set the environment variable? 

BTW: I am using Ubuntu 6.06LTS and the programming language is fortran.

Thanks!

---

### Post by mlind on 2006-08-28
Output text says it:
> 
Either use on the make command line:
  make MACHINE=target
or define the environment variable MACHINE by:
  export MACHINE=target


if you use export, the variable is effective for current terminal session.
```

export MACHINE=*target*
make -k all

```

or you can define variable only for make instance
```

MACHINE=*target* make -k all

```

---

