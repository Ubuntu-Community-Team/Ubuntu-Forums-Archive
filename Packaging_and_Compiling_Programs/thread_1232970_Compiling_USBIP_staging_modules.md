---
title: "Compiling USBIP staging modules"
date: 2009-08-06
forum: Packaging and Compiling Programs
---

### Post by Leslie Viljoen on 2009-08-06
I am trying to compile a client for the USBIP project here: [http://usbip.sourceforge.net](http://usbip.sourceforge.net)

The client needs two drivers to be built, and for 2.6.28+ kernels there is a note saying "try linux staging!". From that cryptic instruction I have noticed that I can go to my kernel headers in /usr/src/linux/linux-headers-2.6.28-13-generic, run "sudo make menuconfig" and find the drivers I want under:

```

     -> Device Drivers                    
       -> Staging drivers&#9474;  
         -> Exclude Staging drivers from being built = n
           -> USB IP support (EXPERIMENTAL) 

```

Now, I can select the modules there but I don't know the next steps. I have tried "sudo make modules" but I get:

```

  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[1]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make: *** [prepare0] Error 2

```

Reading up on compiling kernels it is not clear to me if I need the full kernel source or can get by with just the headers. What say the gurus? :-)

---

### Post by Leslie Viljoen on 2009-08-07
I have managed to start actually compiling by installing the full linux source and also "build dep linux". I really only want to compile two tiny modules but I don't know how to do that, so I did a "sudo make modules". This eventually compiled the ones I wanted in drivers/staging/usbip. So then I copied them by hand into my running kernel's /lib/modules directory (after backing it up) and ran 'sudo depmod'.

Now, running "sudo modprobe usbip_common_mod" gives:
FATAL: Error inserting usbip_common_mod (/lib/modules/2.6.28-13-generic.ksplice-updates/kernel/drivers/staging/usbip/usbip_common_mod.ko): Invalid module format

I have tried using '-f', so it seems its not just a versioning problem. As you can see I am using KSplice too - not sure if that makes any difference.

Can someone suggest what I did wrong?

---

