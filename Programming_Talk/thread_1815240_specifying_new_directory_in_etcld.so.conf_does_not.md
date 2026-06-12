---
title: "specifying new directory in /etc/ld.so.conf does not seem to work"
date: 2011-07-30
forum: Programming Talk
---

### Post by quickk on 2011-07-30
Hi everyone, 

    I'm trying to use a minimum perfect hash library called cmph.  I've compiled it and installed the library to the folder /opt/local/lib.  Then I added that folder to the /etc/ld.so.conf file like this:

```
/opt/local/lib
include /etc/ld.so.conf.d/*.conf

```

(that last line was already there)

I then ran "sudo ldconfig" to refresh the library cache.

The problem is that when I try to compile my program, I get the message that the cmph library cannot be found

```
mpiifort -fPIC -o sim sim.f90 kinds_module.o variables_module.o basis_module.o Hamiltonian_module.o mph.o -lcmph
ld: cannot find -lcmph

```

However when I instead use the -L/opt/local/lib option everything works great: (I get no errors, and can run my program)

```
mpiifort -fPIC -o sim sim.f90 kinds_module.o variables_module.o basis_module.o Hamiltonian_module.o mph.o -L/opt/local/lib -lcmph
```
 
I obviously don't understand something.  I thought that both approaches would work equally well.   Any comments?

---

### Post by soltanis on 2011-07-30
Not entirely sure but it might be that ldconfig sets LD_LIBRARY_PATH, so consider restarting your shell and seeing if that changes anything.

---

### Post by johnl on 2011-07-31
At compile time, the compile-time linker, **ld**, needs to know where to find shared libraries to link to.  This is specified, as you noticed, with the **-L/path/to/lib** argument to ld.  You can view the default arguments for this with **gcc -print-search-dirs**.

At runtime, the OS needs to know where shared libraries linked to an executable can be found so that they can be loaded when the program is executed.  This is specified in **LD_LIBRARY_PATH** or **ld.so.conf**.

These configurations don't overlap, so you will need to do both.

---

### Post by quickk on 2011-08-01
Thank you jonhl!  That made perfect sense.  You wouldn't believe much time I've spent trying to understand this.   I'm slowly getting learning the ropes, but I still have a long way to go.

---

### Post by dwhitney67 on 2011-08-01
> **johnl said:**
> This is specified in **LD_LIBRARY_PATH** or **ld.so.conf**.

These configurations don't overlap, so you will need to do both.

The word "or" in your first statement contradicts what you state in your second statement.

The use of LD_LIBRARY_PATH is only required for library paths that are NOT in the ld cache.  One can verify what paths (and hence libraries) are in the ld-cache by running the ldconfig command with the -v option.

As for the OP editing /etc/ld.so.conf, personally I would have recommended that he create a file in /etc/ld.so.conf.d directory that contains the library path that is required. Then run ldconfig (with the -v option) to verify that the library has been found and placed in the cache.

---

### Post by johnl on 2011-08-01
> **dwhitney67 said:**
> The word "or" in your first statement contradicts what you state in your second statement.

The use of LD_LIBRARY_PATH is only required for library paths that are NOT in the ld cache.  One can verify what paths (and hence libraries) are in the ld-cache by running the ldconfig command with the -v option.

As for the OP editing /etc/ld.so.conf, personally I would have recommended that he create a file in /etc/ld.so.conf.d directory that contains the library path that is required. Then run ldconfig (with the -v option) to verify that the library has been found and placed in the cache.

Sorry, that was unclear; what I meant was:

```
pass_dash_L_to_ld && (specify_LD_LIBRARY_PATH || add_entry_to_ld.so.conf)
```

You need to do both the first step and one of the latter steps.

---

