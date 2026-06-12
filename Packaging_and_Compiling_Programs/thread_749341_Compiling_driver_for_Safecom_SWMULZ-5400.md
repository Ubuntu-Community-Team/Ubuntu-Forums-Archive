---
title: "Compiling driver for Safecom SWMULZ-5400"
date: 2008-04-08
forum: Packaging and Compiling Programs
---

### Post by TimGS on 2008-04-08
See [http://ubuntuforums.org/showthread.php?p=4563951](http://ubuntuforums.org/showthread.php?p=4563951)

I have been trying to compile the above driver with little sucess. The current stumbling block is that one of the .c files is wanting to include some .h files from a non-existent subdirectory ('linux') within the set of files I downloaded from Safecom. See posts 7 and 8 in the above thread.

I gather another line of attack is to try the windows driver in ndiswrapper. I'll be trying that if its suggested that I'm banging my head against a brick wall in trying to compile the 'proper' linux driver.

-- Tim.
](*,)

---

### Post by geraldm on 2008-04-08
I did not see the file you downloaded from savecom, nor could I find a url.  This is just a guess, after seeing the thread:

There are two directories involved.  The "config.h" may possibly be the
file ".config.h"  in the top source directory when building the linux kernel.  This file may be moved and renamed and some distros will add the kernel version as a suffix, e.g /boot/config-2.6.24.2n.  The file should have information on the wireless options selected for the kernel.

The other *.h files should be in the kernel source subdirectory $TOP/include/linux/udp.h   These should be in the kernel headers for the distro and version you are using, the *-dev package for the headers.

You should be able to get by with the proper headers, and a correct Makefile.

Gerald

---

### Post by TimGS on 2008-04-15
I now get 
> tim@zebedee:~/WLANfiles/Linux-Driver$ make 
make both
make[1]: Entering directory `/home/tim/WLANfiles/Linux-Driver'
make clean
make[2]: Entering directory `/home/tim/WLANfiles/Linux-Driver'
rm -rf .tmp_versions .*.cmd *.ko *.mod.c *.mod.o *.o src/*.o  src/.*.o.cmd menudbg apdbg
make[2]: Leaving directory `/home/tim/WLANfiles/Linux-Driver'
make ZD1211REV_B=0
make[2]: Entering directory `/home/tim/WLANfiles/Linux-Driver'
/lib/modules/2.6.22-14-generic/build
/home/tim/WLANfiles/Linux-Driver
-I/home/tim/WLANfiles/Linux-Driver/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZDCONF_MENUDBG -DZDCONF_APDBG -DZD1211
src/zd1205.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zddebug2.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/tim/WLANfiles/Linux-Driver
make[3]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  LD      /home/tim/WLANfiles/Linux-Driver/built-in.o
  CC [M]  /home/tim/WLANfiles/Linux-Driver/src/zd1205.o
In file included from /home/tim/WLANfiles/Linux-Driver/src/zd1205.c:42:
/home/tim/WLANfiles/Linux-Driver/src/zd1205.h:663: warning: '__packed__' attribute ignored
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:244: warning: function declaration isn't a prototype
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:245: warning: function declaration isn't a prototype
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:312: warning: useless storage class specifier in empty declaration
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:439: error: expected declaration specifiers or '...' before 'write'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:439: error: expected declaration specifiers or '...' before 'fd'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:439: error: expected declaration specifiers or '...' before 'buf'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:439: error: expected declaration specifiers or '...' before 'count'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:440: warning: type defaults to 'int' in declaration of '_syscall3'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:440: error: expected ',' or ';' before '_syscall3'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:445: error: 'dot11A_Channel' undeclared here (not in a function)
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_house_keeping':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:1441: warning: unused variable 'tmpvalue'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_config':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:2313: warning: format '%d' expects type 'int', but argument 2 has type 'U32'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_validate_frame':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:2688: warning: unused variable 'len1'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_rx_isr':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:3927: error: 'struct sk_buff' has no member named 'mac'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_close':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:4608: warning: implicit declaration of function 're_initFdescBuf'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_xmit_frame':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:4701: warning: suggest parentheses around && within ||
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_watchdog':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:5335: warning: unused variable 'ssidLenToDump'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:5334: warning: unused variable 'cbTemp'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_ioctl_setiwencode':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:5724: warning: unused variable 'bReconnect'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205wext_siwscan':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:6595: warning: implicit declaration of function 'zd_CmdProbeReq'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:6539: warning: unused variable 'ul_mac_ps_state'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:6538: warning: unused variable 'oldMacMode'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:6537: warning: unused variable 'i'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_translate_scan':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:6715: warning: unknown conversion type character ',' in format
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:6715: warning: spurious trailing '%' in format
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_list_bss':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:6891: warning: spurious trailing '%' in format
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_ioctl':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:7163: warning: implicit declaration of function 'verify_area'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:7572: warning: ISO C90 forbids mixed declarations and code
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_load_card_setting':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:7940: warning: implicit declaration of function 'open'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:7957: warning: implicit declaration of function 'read'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:7961: warning: implicit declaration of function 'close'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:7967: warning: suggest parentheses around assignment used as truth value
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_save_card_setting':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:8113: warning: implicit declaration of function 'write'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zdcb_AssocRequest':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:9153: warning: implicit declaration of function 'HashSearch'
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:9153: warning: assignment makes pointer from integer without a cast
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'zd1205_set_zd_cbs':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:9209: warning: assignment from incompatible pointer type
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c: In function 'CalculateQuality':
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:9423: warning: ISO C90 forbids mixed declarations and code
/home/tim/WLANfiles/Linux-Driver/src/zd1205.c:9425: warning: unused variable 'rxOffset'
make[4]: *** [/home/tim/WLANfiles/Linux-Driver/src/zd1205.o] Error 1
make[3]: *** [_module_/home/tim/WLANfiles/Linux-Driver] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/tim/WLANfiles/Linux-Driver'
make[1]: *** [both] Error 2
make[1]: Leaving directory `/home/tim/WLANfiles/Linux-Driver'
make: *** [all] Error 2
tim@zebedee:~/WLANfiles/Linux-Driver$ 


I changed the makefile to include the linux header files:
> INCLUDES=-I$(KERNEL_SOURCE)/include -I$(SRC_DIR)/include/ -I$(SRC_DIR) -I$(KERNEL_SOURCE)/include/linux

Also, it appears that config.h as referenced by zd1205.c may be autoconf.h in my kernel. I say 'maybe' because it still obviously isn't compiling. I did make a symbolic link to autoconf.h named config.h.

I am trying the windows driver with ndiswrapper as mentioned on [http://community.fluxbuntu.org/index.php?topic=472.0](http://community.fluxbuntu.org/index.php?topic=472.0) but with limited success there also.

thanks,
-- Tim.

---

