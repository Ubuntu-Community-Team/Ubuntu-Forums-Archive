---
title: "How to compile modules for release kernels?"
date: 2015-08-05
forum: Packaging and Compiling Programs
---

### Post by twfry on 2015-08-05
I am trying to compile a module for the standard Ubuntu 15.04 kernel as part of a full kernel build, but have been unable to do so because I have been unable to get the vermagic signatures to match correctly. I have tried several things below none of which worked. Compiling just the module against the installed kernel headers does work, but I don't understand how to make it work as part of a full build against any version.

After installing 15.04 the kernel name is "3.19.0-15-generic" and the installed kernel module vermagic tags are as below:
```

zaphod@ubuntu:~$ uname -r
3.19.0-15-generic
zaphod@ubuntu:~$ modinfo cupid.ko
vermagic:       3.19.0-15-generic SMP mod_unload modversions 
```

I tried to download the matching Ubuntu git repository with the following:
```

zaphod@ubuntu:~$ git clone git://kernel.ubuntu.com/ubuntu/ubuntu-vivid.git
zaphod@ubuntu:~$ git checkout Ubuntu-3.19.0-15.15
zaphod@ubuntu:~$ cp /boot/config-3.19.0-15-generic ./.config
zaphod@ubuntu:~$ make
```

However when I check the resulting vermagic tag in either standard modules or my test module the tag is as below, which does not match the standard installed 15.04 kernel above and the load fails.
```

zaphod@ubuntu:~$ modinfo helloworld.ko
vermagic:       3.19.3 SMP mod_unload modversions 
```

I have also tried downloading the git repository from kernel.org, checking out v3.19.0, matching the SUBLEVEL and EXTRAVERSION tags in the Makefile to specify 3.19.0-15-generic, but this too fails to make loadable modules because an extra "+" is added to the end which causes a mismatch.
```

zaphod@ubuntu:~$ modinfo helloworld.ko
vermagic:       3.19.0-15-generic+ SMP mod_unload modversions
```

The only thing that HAS worked is to independently compile the module against the installed kernel headers independently without compiling the rest of the kernel, i.e. with the following Makefile
```

obj-m                += helloworld.o
all:
    make -C /lib/modules/$(shell uname -r)/build/ M=$(PWD) modules
clean:
    make -C /lib/modules/$(shell uname -r)/build/ M=$(PWD) clean
```

_The problem with this_ is the only way I've found to compile a module for a Ubuntu kernel is to compile the module against a running system with a matching kernel version running. However I'd like to compile the module for any kernel version that may be needed. 

If anyone can clear this up that would be great. Thanks,

---

