---
title: "How install huawei e303c driver in ubuntu 10.04 and connect to net"
date: 2012-12-30
forum: New to Ubuntu
---

### Post by greattime on 2012-12-30
hi i have installed the drivers as given in the huawei manual, but got lot of errors while installing and not able to connect to net, i am posting the output of installation here, hope somebody can help me 

[COLOR=Navy]DRIVER COPY START
STA_PATH_FLAG=.
STA_PATH_FULL=/root/Desktop/driver/install
START_PATH_DRIVER=/root/Desktop/driver
CURRENT install from ./install
INSTALL_PATH=/root/Desktop
DRIVER COPY END
have usb_modeswitch rules to HUAWEI DataCard: COUNT=0
3
ttyUSB%n COUNT=3
1-1:1.3 unbind and bind option
COUNT_END=2
1-1:1.2 unbind and bind option
COUNT_END=1
1-1:1.0 unbind and bind option
COUNT_END=0
ERROR: Removing 'cdc_ether': No such file or directory
ERROR: Removing 'usbnet': No such file or directory
ERROR: Removing 'hw_cdc_driver': No such file or directory
make -C src/ clean
make[1]: Entering directory `/root/Desktop/driver/ndis_driver/ndis_src/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers *.order
/root/Desktop/driver/ndis_driver/ndis_src/src/add_header.sh  "clean" "/lib/modules/3.0.0-23-generic/build/include/linux/usb"
rmmod -f hw_cdc_driver
ERROR: Removing 'hw_cdc_driver': No such file or directory
make[1]: *** [clean] Error 1
make[1]: Leaving directory `/root/Desktop/driver/ndis_driver/ndis_src/src'
make: *** [clean] Error 2
make -C src/ modules
make[1]: Entering directory `/root/Desktop/driver/ndis_driver/ndis_src/src'
#/root/Desktop/driver/ndis_driver/ndis_src/src/add_header.sh  "modules" "/lib/modules/3.0.0-23-generic/build/include/linux/usb"
make -C /lib/modules/3.0.0-23-generic/build SUBDIRS=/root/Desktop/driver/ndis_driver/ndis_src/src modules
make[2]: Entering directory `/usr/src/linux-headers-3.0.0-23-generic'
  CC [M]  /root/Desktop/driver/ndis_driver/ndis_src/src/hw_cdc_driver.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /root/Desktop/driver/ndis_driver/ndis_src/src/hw_cdc_driver.mod.o
  LD [M]  /root/Desktop/driver/ndis_driver/ndis_src/src/hw_cdc_driver.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.0.0-23-generic'
strip --strip-debug hw_cdc_driver.o
make[1]: Leaving directory `/root/Desktop/driver/ndis_driver/ndis_src/src'
make -C src/ install
make[1]: Entering directory `/root/Desktop/driver/ndis_driver/ndis_src/src'
#install -m 744 -c hw_cdc_driver.o /lib/modules/3.0.0-23-generic/kernel/drivers/usb/net
#depmod -a
#modprobe hw_cdc_driver
/root/Desktop/driver/ndis_driver/ndis_src/src/add_header.sh  "install"
modprobe hw_cdc_driver
make[1]: Leaving directory `/root/Desktop/driver/ndis_driver/ndis_src/src'

The Linux NDIS driver is installed successfully.
USBSERIAL_TARGET_PATH = 
ACM_TARGET_PATH = 
ADDRUNLEVEL=/etc/rc3.d
`/etc/rc3.d/S99runhwactivator' -> `/etc/init.d/runhwactivator'
`/etc/rc3.d/K10runhwactivator' -> `/etc/init.d/runhwactivator'
ADDRUNLEVEL=/etc/rc2.d
`/etc/rc2.d/S99runhwactivator' -> `/etc/init.d/runhwactivator'
`/etc/rc2.d/K10runhwactivator' -> `/etc/init.d/runhwactivator'
ADDRUNLEVEL=/etc/rc4.d
`/etc/rc4.d/S99runhwactivator' -> `/etc/init.d/runhwactivator'
`/etc/rc4.d/K10runhwactivator' -> `/etc/init.d/runhwactivator'
ADDRUNLEVEL=/etc/rc5.d
`/etc/rc5.d/S99runhwactivator' -> `/etc/init.d/runhwactivator'
`/etc/rc5.d/K10runhwactivator' -> `/etc/init.d/runhwactivator'
qmi_wwan interface not exist,ok
[/COLOR]
in network manager the device is not shown, and pon gives no error but not connecting to net.

---

