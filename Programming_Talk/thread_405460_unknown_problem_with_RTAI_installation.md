---
title: "unknown problem with RTAI installation"
date: 2007-04-09
forum: Programming Talk
---

### Post by Alphi on 2007-04-09
this is the entire makefile, what i believe to be the useful portion is just at the bottom.  So far i have run into numerous problems with the installation of RTAI, so the errors i am encountering now aren't entirely unexpected to me.  That being said i couldn't find anything relating to this, and any help would be greatly appreciated.

Regards,

Philippe


make  all-recursive
make[1]: Entering directory `/home/alphi/rtai-3.3'
****************************************
*  Your RTAI configuration has changed *
*  forcing 'make clean' ...            *
****************************************
make[2]: Entering directory `/home/alphi/rtai-3.3'
Making clean in rtai-lab
make[3]: Entering directory `/home/alphi/rtai-3.3/rtai-lab'
Making clean in matlab
make[4]: Entering directory `/home/alphi/rtai-3.3/rtai-lab/matlab'
rm -rf .libs _libs
rm -f *.lo
make[4]: Leaving directory `/home/alphi/rtai-3.3/rtai-lab/matlab'
Making clean in scilab
make[4]: Entering directory `/home/alphi/rtai-3.3/rtai-lab/scilab'
Making clean in utility
make[5]: Entering directory `/home/alphi/rtai-3.3/rtai-lab/scilab/utility'
rm -rf .libs _libs
rm -f *.lo
make[5]: Leaving directory `/home/alphi/rtai-3.3/rtai-lab/scilab/utility'
Making clean in devices
make[5]: Entering directory `/home/alphi/rtai-3.3/rtai-lab/scilab/devices'
test -z "libsciblk.a" || rm -f libsciblk.a
rm -rf .libs _libs
rm -f *.o
rm -f *.lo
make[5]: Leaving directory `/home/alphi/rtai-3.3/rtai-lab/scilab/devices'
Making clean in .
make[5]: Entering directory `/home/alphi/rtai-3.3/rtai-lab/scilab'
rm -rf .libs _libs
rm -f *.lo
make[5]: Leaving directory `/home/alphi/rtai-3.3/rtai-lab/scilab'
make[4]: Leaving directory `/home/alphi/rtai-3.3/rtai-lab/scilab'
Making clean in .
make[4]: Entering directory `/home/alphi/rtai-3.3/rtai-lab'
 rm -f xrtailab xrtailab
rm -rf .libs _libs
rm -f *.o
rm -f *.lo
make[4]: Leaving directory `/home/alphi/rtai-3.3/rtai-lab'
make[3]: Leaving directory `/home/alphi/rtai-3.3/rtai-lab'
Making clean in addons
make[3]: Entering directory `/home/alphi/rtai-3.3/addons'
Making clean in comedi
make[4]: Entering directory `/home/alphi/rtai-3.3/addons/comedi'
test -z "libkcomedilxrt.a" || rm -f libkcomedilxrt.a
rm -rf .libs _libs
rm -f *.ko *.mod.c .*.cmd *.o
test -z "" || rm -f
rm -f *.o
rm -f *.lo
make[4]: Leaving directory `/home/alphi/rtai-3.3/addons/comedi'
Making clean in drivers
make[4]: Entering directory `/home/alphi/rtai-3.3/addons/drivers'
Making clean in serial
make[5]: Entering directory `/home/alphi/rtai-3.3/addons/drivers/serial'
rm -rf .libs _libs
rm -f *.ko *.mod.c .*.cmd *.o
test -z "" || rm -f
rm -f *.o
rm -f *.lo
make[5]: Leaving directory `/home/alphi/rtai-3.3/addons/drivers/serial'
Making clean in .
make[5]: Entering directory `/home/alphi/rtai-3.3/addons/drivers'
rm -rf .libs _libs
rm -f *.lo
make[5]: Leaving directory `/home/alphi/rtai-3.3/addons/drivers'
make[4]: Leaving directory `/home/alphi/rtai-3.3/addons/drivers'
Making clean in .
make[4]: Entering directory `/home/alphi/rtai-3.3/addons'
rm -rf .libs _libs
rm -f *.lo
make[4]: Leaving directory `/home/alphi/rtai-3.3/addons'
make[3]: Leaving directory `/home/alphi/rtai-3.3/addons'
Making clean in testsuite
make[3]: Entering directory `/home/alphi/rtai-3.3/testsuite'
Making clean in user
make[4]: Entering directory `/home/alphi/rtai-3.3/testsuite/user'
Making clean in switches
make[5]: Entering directory `/home/alphi/rtai-3.3/testsuite/user/switches'
rm -rf .libs _libs
 rm -f switches switches
rm -f *.o
rm -f *.lo
make[5]: Leaving directory `/home/alphi/rtai-3.3/testsuite/user/switches'
Making clean in preempt
make[5]: Entering directory `/home/alphi/rtai-3.3/testsuite/user/preempt'
rm -rf .libs _libs
 rm -f preempt preempt
 rm -f display display
rm -f *.o
rm -f *.lo
make[5]: Leaving directory `/home/alphi/rtai-3.3/testsuite/user/preempt'
Making clean in latency
make[5]: Entering directory `/home/alphi/rtai-3.3/testsuite/user/latency'
rm -rf .libs _libs
 rm -f latency latency
 rm -f display display
rm -f *.o
rm -f *.lo
make[5]: Leaving directory `/home/alphi/rtai-3.3/testsuite/user/latency'
Making clean in .
make[5]: Entering directory `/home/alphi/rtai-3.3/testsuite/user'
rm -rf .libs _libs
rm -f *.lo
make[5]: Leaving directory `/home/alphi/rtai-3.3/testsuite/user'
make[4]: Leaving directory `/home/alphi/rtai-3.3/testsuite/user'
Making clean in kern
make[4]: Entering directory `/home/alphi/rtai-3.3/testsuite/kern'
Making clean in switches
make[5]: Entering directory `/home/alphi/rtai-3.3/testsuite/kern/switches'
rm -rf .libs _libs
rm -f *.ko *.mod.c .*.cmd *.o
test -z "" || rm -f
rm -f *.o
rm -f *.lo
make[5]: Leaving directory `/home/alphi/rtai-3.3/testsuite/kern/switches'
Making clean in preempt
make[5]: Entering directory `/home/alphi/rtai-3.3/testsuite/kern/preempt'
rm -rf .libs _libs
rm -f *.ko *.mod.c .*.cmd *.o
test -z "" || rm -f
 rm -f display display
rm -f *.o
rm -f *.lo
make[5]: Leaving directory `/home/alphi/rtai-3.3/testsuite/kern/preempt'
Making clean in latency
make[5]: Entering directory `/home/alphi/rtai-3.3/testsuite/kern/latency'
rm -rf .libs _libs
rm -f *.ko *.mod.c .*.cmd *.o
test -z "" || rm -f
 rm -f display display
rm -f *.o
rm -f *.lo
make[5]: Leaving directory `/home/alphi/rtai-3.3/testsuite/kern/latency'
Making clean in .
make[5]: Entering directory `/home/alphi/rtai-3.3/testsuite/kern'
rm -rf .libs _libs
rm -f *.lo
make[5]: Leaving directory `/home/alphi/rtai-3.3/testsuite/kern'
make[4]: Leaving directory `/home/alphi/rtai-3.3/testsuite/kern'
Making clean in .
make[4]: Entering directory `/home/alphi/rtai-3.3/testsuite'
rm -rf .libs _libs
rm -f *.lo
make[4]: Leaving directory `/home/alphi/rtai-3.3/testsuite'
make[3]: Leaving directory `/home/alphi/rtai-3.3/testsuite'
Making clean in doc
make[3]: Entering directory `/home/alphi/rtai-3.3/doc'
Making clean in doxygen
make[4]: Entering directory `/home/alphi/rtai-3.3/doc/doxygen'
rm -rf .libs _libs
rm -f *.lo
make[4]: Leaving directory `/home/alphi/rtai-3.3/doc/doxygen'
Making clean in docbook
make[4]: Entering directory `/home/alphi/rtai-3.3/doc/docbook'
Making clean in docbook-test
make[5]: Entering directory `/home/alphi/rtai-3.3/doc/docbook/docbook-test'
rm -rf .libs _libs
rm -f *.lo
make[5]: Leaving directory `/home/alphi/rtai-3.3/doc/docbook/docbook-test'
Making clean in custom-stylesheets
make[5]: Entering directory `/home/alphi/rtai-3.3/doc/docbook/custom-stylesheets'
Making clean in xsl
make[6]: Entering directory `/home/alphi/rtai-3.3/doc/docbook/custom-stylesheets/xsl'
Making clean in html
make[7]: Entering directory `/home/alphi/rtai-3.3/doc/docbook/custom-stylesheets/xsl/html'
test -z "rtai-titlepage.xsl" || rm -f rtai-titlepage.xsl
rm -rf .libs _libs
rm -f *.lo
make[7]: Leaving directory `/home/alphi/rtai-3.3/doc/docbook/custom-stylesheets/xsl/html'
Making clean in fo
make[7]: Entering directory `/home/alphi/rtai-3.3/doc/docbook/custom-stylesheets/xsl/fo'
rm -rf .libs _libs
rm -f *.lo
make[7]: Leaving directory `/home/alphi/rtai-3.3/doc/docbook/custom-stylesheets/xsl/fo'
Making clean in common
make[7]: Entering directory `/home/alphi/rtai-3.3/doc/docbook/custom-stylesheets/xsl/common'
rm -rf .libs _libs
rm -f *.lo
make[7]: Leaving directory `/home/alphi/rtai-3.3/doc/docbook/custom-stylesheets/xsl/common'
Making clean in .
make[7]: Entering directory `/home/alphi/rtai-3.3/doc/docbook/custom-stylesheets/xsl'
rm -rf .libs _libs
rm -f *.lo
make[7]: Leaving directory `/home/alphi/rtai-3.3/doc/docbook/custom-stylesheets/xsl'
make[6]: Leaving directory `/home/alphi/rtai-3.3/doc/docbook/custom-stylesheets/xsl'
Making clean in .
make[6]: Entering directory `/home/alphi/rtai-3.3/doc/docbook/custom-stylesheets'
rm -rf .libs _libs
rm -f *.lo
make[6]: Leaving directory `/home/alphi/rtai-3.3/doc/docbook/custom-stylesheets'
make[5]: Leaving directory `/home/alphi/rtai-3.3/doc/docbook/custom-stylesheets'
Making clean in .
make[5]: Entering directory `/home/alphi/rtai-3.3/doc/docbook'
rm -rf .libs _libs
rm -f *.lo
make[5]: Leaving directory `/home/alphi/rtai-3.3/doc/docbook'
make[4]: Leaving directory `/home/alphi/rtai-3.3/doc/docbook'
Making clean in .
make[4]: Entering directory `/home/alphi/rtai-3.3/doc'
rm -rf .libs _libs
rm -f *.lo
make[4]: Leaving directory `/home/alphi/rtai-3.3/doc'
make[3]: Leaving directory `/home/alphi/rtai-3.3/doc'
Making clean in base
make[3]: Entering directory `/home/alphi/rtai-3.3/base'
Making clean in scripts
make[4]: Entering directory `/home/alphi/rtai-3.3/base/scripts'
rm -rf .libs _libs
rm -f *.lo
make[4]: Leaving directory `/home/alphi/rtai-3.3/base/scripts'
Making clean in arch
make[4]: Entering directory `/home/alphi/rtai-3.3/base/arch'
Making clean in i386
make[5]: Entering directory `/home/alphi/rtai-3.3/base/arch/i386'
Making clean in calibration
make[6]: Entering directory `/home/alphi/rtai-3.3/base/arch/i386/calibration'
 rm -f calibrate calibrate
 rm -f calibration_helper calibration_helper
rm -rf .libs _libs
rm -f *.ko *.mod.c .*.cmd *.o
test -z "" || rm -f
rm -f *.o
rm -f *.lo
make[6]: Leaving directory `/home/alphi/rtai-3.3/base/arch/i386/calibration'
Making clean in hal
make[6]: Entering directory `/home/alphi/rtai-3.3/base/arch/i386/hal'
rm -rf .libs _libs
rm -f *.ko *.mod.c .*.cmd *.o
test -z "" || rm -f
rm -f *.o
rm -f *.lo
make[6]: Leaving directory `/home/alphi/rtai-3.3/base/arch/i386/hal'
Making clean in .
make[6]: Entering directory `/home/alphi/rtai-3.3/base/arch/i386'
rm -rf .libs _libs
rm -f *.lo
make[6]: Leaving directory `/home/alphi/rtai-3.3/base/arch/i386'
make[5]: Leaving directory `/home/alphi/rtai-3.3/base/arch/i386'
Making clean in .
make[5]: Entering directory `/home/alphi/rtai-3.3/base/arch'
rm -rf .libs _libs
rm -f *.lo
make[5]: Leaving directory `/home/alphi/rtai-3.3/base/arch'
make[4]: Leaving directory `/home/alphi/rtai-3.3/base/arch'
Making clean in sched
make[4]: Entering directory `/home/alphi/rtai-3.3/base/sched'
Making clean in liblxrt
make[5]: Entering directory `/home/alphi/rtai-3.3/base/sched/liblxrt'
test -z "liblxrt.la" || rm -f liblxrt.la
rm -f "./so_locations"
rm -rf .libs _libs
rm -f *.o
rm -f *.lo
make[5]: Leaving directory `/home/alphi/rtai-3.3/base/sched/liblxrt'
Making clean in .
make[5]: Entering directory `/home/alphi/rtai-3.3/base/sched'
rm -rf .libs _libs
rm -f *.ko *.mod.c .*.cmd *.o
test -z "      " || rm -f
rm -f *.o
rm -f *.lo
make[5]: Leaving directory `/home/alphi/rtai-3.3/base/sched'
make[4]: Leaving directory `/home/alphi/rtai-3.3/base/sched'
Making clean in leds
make[4]: Entering directory `/home/alphi/rtai-3.3/base/leds'
rm -rf .libs _libs
rm -f *.ko *.mod.c .*.cmd *.o
test -z "" || rm -f
rm -f *.o
rm -f *.lo
make[4]: Leaving directory `/home/alphi/rtai-3.3/base/leds'
Making clean in wd
make[4]: Entering directory `/home/alphi/rtai-3.3/base/wd'
rm -rf .libs _libs
rm -f *.ko *.mod.c .*.cmd *.o
test -z "" || rm -f
rm -f *.o
rm -f *.lo
make[4]: Leaving directory `/home/alphi/rtai-3.3/base/wd'
Making clean in usi
make[4]: Entering directory `/home/alphi/rtai-3.3/base/usi'
rm -rf .libs _libs
rm -f *.ko *.mod.c .*.cmd *.o
test -z "" || rm -f
rm -f *.o
rm -f *.lo
make[4]: Leaving directory `/home/alphi/rtai-3.3/base/usi'
Making clean in tasklets
make[4]: Entering directory `/home/alphi/rtai-3.3/base/tasklets'
rm -rf .libs _libs
rm -f *.ko *.mod.c .*.cmd *.o
test -z "" || rm -f
rm -f *.o
rm -f *.lo
make[4]: Leaving directory `/home/alphi/rtai-3.3/base/tasklets'
Making clean in malloc
make[4]: Entering directory `/home/alphi/rtai-3.3/base/malloc'
rm -rf .libs _libs
test -z "" || rm -f
rm -f *.o
rm -f *.lo
make[4]: Leaving directory `/home/alphi/rtai-3.3/base/malloc'
Making clean in math
make[4]: Entering directory `/home/alphi/rtai-3.3/base/math'
rm -rf .libs _libs
rm -f *.ko *.mod.c .*.cmd *.o
test -z "" || rm -f
rm -f *.o
rm -f *.lo
make[4]: Leaving directory `/home/alphi/rtai-3.3/base/math'
Making clean in ipc
make[4]: Entering directory `/home/alphi/rtai-3.3/base/ipc'
Making clean in mq
make[5]: Entering directory `/home/alphi/rtai-3.3/base/ipc/mq'
rm -rf .libs _libs
rm -f *.ko *.mod.c .*.cmd *.o
test -z "" || rm -f
rm -f *.o
rm -f *.lo
make[5]: Leaving directory `/home/alphi/rtai-3.3/base/ipc/mq'
Making clean in tbx
make[5]: Entering directory `/home/alphi/rtai-3.3/base/ipc/tbx'
rm -rf .libs _libs
rm -f *.ko *.mod.c .*.cmd *.o
test -z "" || rm -f
rm -f *.o
rm -f *.lo
make[5]: Leaving directory `/home/alphi/rtai-3.3/base/ipc/tbx'
Making clean in mbx
make[5]: Entering directory `/home/alphi/rtai-3.3/base/ipc/mbx'
rm -rf .libs _libs
rm -f *.ko *.mod.c .*.cmd *.o
test -z "" || rm -f
rm -f *.o
rm -f *.lo
make[5]: Leaving directory `/home/alphi/rtai-3.3/base/ipc/mbx'
Making clean in msg
make[5]: Entering directory `/home/alphi/rtai-3.3/base/ipc/msg'
rm -rf .libs _libs
rm -f *.ko *.mod.c .*.cmd *.o
test -z "" || rm -f
rm -f *.o
rm -f *.lo
make[5]: Leaving directory `/home/alphi/rtai-3.3/base/ipc/msg'
Making clean in sem
make[5]: Entering directory `/home/alphi/rtai-3.3/base/ipc/sem'
rm -rf .libs _libs
rm -f *.ko *.mod.c .*.cmd *.o
test -z "" || rm -f
rm -f *.o
rm -f *.lo
make[5]: Leaving directory `/home/alphi/rtai-3.3/base/ipc/sem'
Making clean in shm
make[5]: Entering directory `/home/alphi/rtai-3.3/base/ipc/shm'
rm -rf .libs _libs
rm -f *.ko *.mod.c .*.cmd *.o
test -z "" || rm -f
rm -f *.o
rm -f *.lo
make[5]: Leaving directory `/home/alphi/rtai-3.3/base/ipc/shm'
Making clean in netrpc
make[5]: Entering directory `/home/alphi/rtai-3.3/base/ipc/netrpc'
rm -rf .libs _libs
rm -f *.ko *.mod.c .*.cmd *.o
test -z "" || rm -f
rm -f *.o
rm -f *.lo
make[5]: Leaving directory `/home/alphi/rtai-3.3/base/ipc/netrpc'
Making clean in fifos
make[5]: Entering directory `/home/alphi/rtai-3.3/base/ipc/fifos'
rm -rf .libs _libs
rm -f *.ko *.mod.c .*.cmd *.o
test -z "" || rm -f
rm -f *.o
rm -f *.lo
make[5]: Leaving directory `/home/alphi/rtai-3.3/base/ipc/fifos'
Making clean in bits
make[5]: Entering directory `/home/alphi/rtai-3.3/base/ipc/bits'
rm -rf .libs _libs
rm -f *.ko *.mod.c .*.cmd *.o
test -z "" || rm -f
rm -f *.o
rm -f *.lo
make[5]: Leaving directory `/home/alphi/rtai-3.3/base/ipc/bits'
Making clean in .
make[5]: Entering directory `/home/alphi/rtai-3.3/base/ipc'
rm -rf .libs _libs
rm -f *.lo
make[5]: Leaving directory `/home/alphi/rtai-3.3/base/ipc'
make[4]: Leaving directory `/home/alphi/rtai-3.3/base/ipc'
Making clean in include
make[4]: Entering directory `/home/alphi/rtai-3.3/base/include'
Making clean in asm-i386
make[5]: Entering directory `/home/alphi/rtai-3.3/base/include/asm-i386'
rm -rf .libs _libs
rm -f *.lo
make[5]: Leaving directory `/home/alphi/rtai-3.3/base/include/asm-i386'
Making clean in .
make[5]: Entering directory `/home/alphi/rtai-3.3/base/include'
rm -rf .libs _libs
rm -f *.lo
make[5]: Leaving directory `/home/alphi/rtai-3.3/base/include'
make[4]: Leaving directory `/home/alphi/rtai-3.3/base/include'
Making clean in .
make[4]: Entering directory `/home/alphi/rtai-3.3/base'
rm -rf .libs _libs
rm -f *.lo
make[4]: Leaving directory `/home/alphi/rtai-3.3/base'
make[3]: Leaving directory `/home/alphi/rtai-3.3/base'
Making clean in .
make[3]: Entering directory `/home/alphi/rtai-3.3'
rm -rf .libs _libs
rm -fr modules .cfchanged
rm -f *.lo
make[3]: Leaving directory `/home/alphi/rtai-3.3'
make[2]: Leaving directory `/home/alphi/rtai-3.3'
Making all in base
make[2]: Entering directory `/home/alphi/rtai-3.3/base'
Making all in include
make[3]: Entering directory `/home/alphi/rtai-3.3/base/include'
Making all in asm-i386
make[4]: Entering directory `/home/alphi/rtai-3.3/base/include/asm-i386'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/alphi/rtai-3.3/base/include/asm-i386'
make[4]: Entering directory `/home/alphi/rtai-3.3/base/include'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/alphi/rtai-3.3/base/include'
make[3]: Leaving directory `/home/alphi/rtai-3.3/base/include'
Making all in ipc
make[3]: Entering directory `/home/alphi/rtai-3.3/base/ipc'
Making all in bits
make[4]: Entering directory `/home/alphi/rtai-3.3/base/ipc/bits'
make[5]: Entering directory `/usr/src/linux-2.6.15'
Makefile:532: /usr/src/linux-2.6.15/arch/i386/Makefile: No such file or directory
make[5]: *** No rule to make target `/usr/src/linux-2.6.15/arch/i386/Makefile'.  Stop.
make[5]: Leaving directory `/usr/src/linux-2.6.15'
make[4]: *** [rtai_bits.ko] Error 2
make[4]: Leaving directory `/home/alphi/rtai-3.3/base/ipc/bits'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/alphi/rtai-3.3/base/ipc'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/alphi/rtai-3.3/base'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/alphi/rtai-3.3'
make: *** [all] Error 2

---

