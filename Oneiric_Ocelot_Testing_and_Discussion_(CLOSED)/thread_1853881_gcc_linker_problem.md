---
title: "gcc linker problem"
date: 2011-10-03
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by schander on 2011-10-03
Hi All,
We have written a shared library and packaged into a deb file.
I can install the deb package fine on 10.10, 11.04 and 11.10b2.
However the problem comes when i try and compile out console application with the shared libraries, which are installed to /usr/lib .
the command line is:
```
gcc -lps3000a -lusb_pico-1.0 PS3000Acon.c -oPS3000Acon
```
This works absolutly fine one 10.10, 11.04. However on 11.10b2 I get errors:
```
/tmp/ccGnbTfk.o: In function `SetDefaults':
PS3000Acon.c:(.text+0x307): undefined reference to `ps3000aSetEts'
PS3000Acon.c:(.text+0x38b): undefined reference to `ps3000aSetChannel'
....
collect2: ld returned 1 exit status
```

If the libraries are uninstalled then I do get the error that the libraries cannot be found:
```
/usr/bin/ld: cannot find -lps3000a
/usr/bin/ld: cannot find -lusb_pico-1.0
collect2: ld returned 1 exit status
```
To me this means that the linker is finding the shared libraries, however not using them.
Anyone have any ideas why this would be the case?

Regards
Satpal

---

### Post by t1497f35 on 2011-10-03
On Ubuntu 11.10+ the "libs" part must be at the end:
```

gcc PS3000Acon.c -oPS3000Acon -lps3000a -lusb_pico-1.0

```

The linking/toolkit transition [was scheduled for Natty ]("https://wiki.ubuntu.com/NattyNarwhal/ToolchainTransition")but was adopted starting with Oneiric.

---

### Post by dargaud on 2011-10-03
> **t1497f35 said:**
> On Ubuntu 11.10+ the "libs" part must be at the end:
If this is true, then this is going to break a HUGE amount of makefiles...

---

### Post by t1497f35 on 2011-10-03
> **dargaud said:**
> If this is true, then this is going to break a HUGE amount of makefiles...
I know, my app also broke and I fixed it in a few seconds. It's a necessary transition and it's easy to fix and a lot of packages have been transitioned already, as you can see by the fact that Oneiric and its apps are up and running.

It's not just Ubuntu, all major distros are transitioning.

---

### Post by schander on 2011-10-03
> **t1497f35 said:**
> On Ubuntu 11.10+ the "libs" part must be at the end:
```

gcc PS3000Acon.c -oPS3000Acon -lps3000a -lusb_pico-1.0

```

The linking/toolkit transition [was scheduled for Natty ]("https://wiki.ubuntu.com/NattyNarwhal/ToolchainTransition")but was adopted starting with Oneiric.

Thanks for the quick reply. 
It will also break lots of IDE's that generate makefile (e.g. Eclipse)

Regards
Satpal

---

