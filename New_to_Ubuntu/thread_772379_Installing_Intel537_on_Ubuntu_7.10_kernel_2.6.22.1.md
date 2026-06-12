---
title: "Installing Intel537 on Ubuntu 7.10 kernel 2.6.22.14?"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by stefaca on 2008-04-28
I have been reading on this and other forums about problems with this modem and drivers for 537. I downloaded drivers from Intel site (*Intel-537EP-2.70.95.0-for-2.6.20.tar.gz*) and did like it sad in Readme file:

&#8226;	unzip,
&#8226;	make clean,
&#8226;	make 537,
&#8226;	make install.

After reseting PC in Network Setting I enable using modem and make KPPP but problem: there is no modem. No modem in dev/modem, dev/ttyS0 and so on.

This is what linux say after installing:

> stefaca@TECHNODROME:~/Intel-537EP-2.70.95.0-for-2.6.20$ make clean

cd coredrv; make clean

make[1]: Entering directory `/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv'

rm -f *.ko *.o *~ core

make[1]: Leaving directory `/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv'

rm -f *.o *.ko

stefaca@TECHNODROME:~/Intel-537EP-2.70.95.0-for-2.6.20$ make 537

   Module precompile check

   Current running kernel is: 2.6.22-14-generic

   /lib/modules...   autoconf.h exists

diff: /boot/vmlinuz.autoconf.h: No such file or directory

   autoconf.h matches running kernel

diff: /boot/vmlinuz.version.h: No such file or directory

   version.h matches running kernel

2.6.22-14-generic

make[1]: Entering directory `/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv'

make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv modules

make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'

  CC [M]  /home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.o

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c: In function &#8216;get_pci_info_537&#8217;:

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:119: warning: &#8216;pci_find_device&#8217; is deprecated (declared at include/linux/pci.h:477)

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:139: warning: &#8216;pci_find_device&#8217; is deprecated (declared at include/linux/pci.h:477)

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:158: warning: &#8216;pci_find_device&#8217; is deprecated (declared at include/linux/pci.h:477)

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:177: warning: &#8216;pci_find_device&#8217; is deprecated (declared at include/linux/pci.h:477)

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:205: warning: &#8216;pci_find_device&#8217; is deprecated (declared at include/linux/pci.h:477)

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:215: warning: &#8216;pci_find_device&#8217; is deprecated (declared at include/linux/pci.h:477)

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:225: warning: &#8216;pci_find_device&#8217; is deprecated (declared at include/linux/pci.h:477)

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:234: warning: &#8216;pci_find_device&#8217; is deprecated (declared at include/linux/pci.h:477)

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:243: warning: &#8216;pci_find_device&#8217; is deprecated (declared at include/linux/pci.h:477)

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:253: warning: &#8216;pci_find_device&#8217; is deprecated (declared at include/linux/pci.h:477)

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:263: warning: &#8216;pci_find_device&#8217; is deprecated (declared at include/linux/pci.h:477)

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:273: warning: &#8216;pci_find_device&#8217; is deprecated (declared at include/linux/pci.h:477)

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c: In function &#8216;softcore_init_struct&#8217;:

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:341: warning: assignment from incompatible pointer type

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c: In function &#8216;open&#8217;:

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:395: warning: &#8216;deprecated_irq_flag&#8217; is deprecated (declared at include/linux/interrupt.h:66)

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:397: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:409: warning: &#8216;pm_register&#8217; is deprecated (declared at include/linux/pm_legacy.h:15)

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c: At top level:

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:770: warning: initialization from incompatible pointer type

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:771: warning: initialization from incompatible pointer type

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:872: warning: initialization makes integer from pointer without a cast

  CC [M]  /home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/clmmain.o

  CC [M]  /home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/rts.o

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/rts.c:80: warning: initialization from incompatible pointer type

  CC [M]  /home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/task.o

  CC [M]  /home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/uart.o

  CC [M]  /home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/wwh_dflt.o

  CC [M]  /home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/locks.o

  CC [M]  /home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial_io.o

  CC [M]  /home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial_ioctl.o

  CC [M]  /home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.o

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c: In function &#8216;init_serial&#8217;:

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c:72: warning: &#8216;pci_find_device&#8217; is deprecated (declared at include/linux/pci.h:477)

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c: In function &#8216;softserial_register_tty&#8217;:

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c:127: warning: assignment from incompatible pointer type

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c:128: warning: assignment from incompatible pointer type

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c:151: warning: assignment from incompatible pointer type

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c: At top level:

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c:190: warning: initialization from incompatible pointer type

  CC [M]  /home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.o

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.c:39: warning: initialization makes integer from pointer without a cast

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.c:48: warning: function declaration isn&#8217;t a prototype

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.c:60: warning: initialization from incompatible pointer type

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.c:61: warning: initialization from incompatible pointer type

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.c:65: warning: function declaration isn&#8217;t a prototype

/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.c:446: warning: initialization from incompatible pointer type

  LD [M]  /home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/Intel537.o

  Building modules, stage 2.

  MODPOST 1 modules

WARNING: could not find /home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/.537core.lib.cmd for /home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/537core.lib

  CC      /home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/Intel537.mod.o

  LD [M]  /home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/Intel537.ko

make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'

make[1]: Leaving directory `/home/stefaca/Intel-537EP-2.70.95.0-for-2.6.20/coredrv'

stefaca@TECHNODROME:~/Intel-537EP-2.70.95.0-for-2.6.20$ make install

rm -f /etc/hamregistry.bin

bash 537_inst

running kernel 2.6.22-14-generic

chmod: cannot access `usrsound': No such file or directory

installing hamregistry, used for persistant storage

install: cannot create regular file `/usr/sbin/hamregistry': Permission denied

installing usrsound, a soft buzzer

install: cannot stat `usrsound': No such file or directory

installing 537 module

install: cannot create regular file `/lib/modules/2.6.22-14-generic/kernel/drivers/char/Intel537.ko': Permission denied

make: *** [install] Error 1

stefaca@TECHNODROME:~/Intel-537EP-2.70.95.0-for-2.6.20$ 

What should I do next?

---

### Post by stefaca on 2008-04-29
anyone?

---

### Post by chuckman78 on 2008-08-06
This might be too late but check this link:

[http://groups.google.com/group/ubuntu-modems/]("http://groups.google.com/group/ubuntu-modems/")

Regards,

Carlos
aka chuckman78.

---

### Post by stefaca on 2008-08-06
> **chuckman78 said:**
> This might be too late but check this link:

[http://groups.google.com/group/ubuntu-modems/]("http://groups.google.com/group/ubuntu-modems/")

Regards,

Carlos
aka chuckman78.

it is too late. I have a external modem and everything is OK now

---

### Post by cgkades on 2008-08-06
> **stefaca said:**
> it is too late. I have a external modem and everything is OK now

If that problem ever comes up again, I noticed you had a lot of permission denied. You might need to issue sudo command in order to configure make and install properly

---

