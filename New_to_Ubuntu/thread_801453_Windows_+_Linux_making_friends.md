---
title: "Windows + Linux making friends"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by UnWarierMage224 on 2008-05-20
Hi folks, 

I'm trying to implement this: 

[http://www.venturecake.com/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/](http://www.venturecake.com/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/)

I downloaded vmware server from their website (the binary tar.gz file)... I extracted the folder to my desktop, navigated to it (as per the instructions here: [http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually](http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually) )

but when I tried the ./configure and make commands, nothing. 
I'm not sure how to install this. (I checked the repos/aptitude, vmware-server is not available). 

Help's appreciated, 

-'Mage

---

### Post by avtolle on 2008-05-20
First question: have you installed build essential? If not, go to Synaptic and search for it, and install from there, if you prefer the GUI method.

---

### Post by UnWarierMage224 on 2008-05-20
Yes, I have build-essential installed.

---

### Post by anystupidname on 2008-05-20
Yea, I believe the problem is actually with whatever instructions you're following for the vmware install.

./vmware-install.pl

is the only command you should need to run once you've extracted the tar...

---

### Post by UnWarierMage224 on 2008-05-20
Problem. 

I ran that command as specified, said yes to every question asked (didn't change any default values). Ran into errors when building the vmmon module. As a result I have an icon for VMWare server in my applications menu but that doesn't run anything. How do I remove vmware completely to reinstall it?

received output: 

```

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:48:
/tmp/vmware-config0/vmmon-only/./include/vm_basic_types.h:161: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config0/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1659: error: ‘struct mm_struct’ has no member named ‘dumpable’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

What to do?

-'Mage

---

### Post by shifty_powers on 2008-05-20
```
sudo ./vmware-uninstall.pl
```

---

### Post by UnWarierMage224 on 2008-05-20
OK, thanks. 

Now I'm trying to figure out what went wrong as I'd really like this to work... What is linux's C compiler? I have G++ installed so I'm not sure what happened...

-'Mage

EDIT: Or is it that vmware server hasn't been updated to work with linux 8.04 yet? 

blahhh...

---

### Post by anystupidname on 2008-05-20
Doh! you'll need the any any patch then...
[http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update115.tar.gz](http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update115.tar.gz)

---

### Post by cjm5229 on 2008-05-20
Try using Virtual Box instead does the same thing and IMHO it works better. There is a Deb file available for Hardy at their Website. [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

---

### Post by UnWarierMage224 on 2008-05-20
> **cjm5229 said:**
> Try using Virtual Box instead does the same thing and IMHO it works better. There is a Deb file available for Hardy at their Website. [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

I will give that a try. Is it a matter of following the posted guide but using virtualbox instead of vmware server?

Thanks, 

-'Mage

---

### Post by UnWarierMage224 on 2008-05-20
> **anystupidname said:**
> Doh! you'll need the any any patch then...
[http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update115.tar.gz](http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update115.tar.gz)

I installed the latest version of the any-any patch and when I go to run vmware I get the following errors: 

```

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

```

I installed GCC 3.4 and GCC 4.2 from synaptic, but I still get those same errors. 

What to do?

-'Mage

---

### Post by anystupidname on 2008-05-21
Man, you're just hitting every possible error along the way...:lolflag:
You can create a symlink to overcome that problem:
[http://ubuntuforums.org/showthread.php?t=363968](http://ubuntuforums.org/showthread.php?t=363968)

cheers :)

---

### Post by UnWarierMage224 on 2008-05-21
Thanks for the tip. 

I actually ended up following the guide on the forums to install vmware and voila, it worked! 

-'mage

---

