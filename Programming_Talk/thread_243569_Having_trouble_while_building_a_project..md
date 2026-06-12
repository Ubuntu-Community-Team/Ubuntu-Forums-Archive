---
title: "Having trouble while building a project."
date: 2006-08-25
forum: Programming Talk
---

### Post by Xiong on 2006-08-25
I am having trouble while building a project. It was shown that i need to set the environment variable as "export MACHINE=target".And target can be linux_pgi,linux_intel and so on.The point is that i don't where to set this environment variable.

Someone help please.

BTW:My programming platform is eclipse and language is fortran.

---

### Post by vijayanand_sodadasi on 2006-08-25
> **Xiong said:**
> ...i need to set the environment variable as "export MACHINE=target".And target can be linux_pgi,linux_intel and so on.The point is that i don't where to set this environment variable.


If you are working on a unix/linux box,  Open a terminal and type this command

```
export MACHINE=target
```

---

### Post by Xiong on 2006-08-25
it does not work. I guess there is a place where i can add "export MACHINE=target"
> make -k all 
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



---

