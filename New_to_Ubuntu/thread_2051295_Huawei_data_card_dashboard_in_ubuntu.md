---
title: "Huawei data card dashboard in ubuntu"
date: 2012-09-01
forum: New to Ubuntu
---

### Post by celebratinglife on 2012-09-01
I bought a huawei e303c data card yesterday. In my ubuntu 10.04 I am able to connect to 3g internet using sakis 3g and network manager.  I also installed mobile partner software for linux provided with the device but I am unable to use the mobile partner software as I am not getting any icon for it. 
Because of the lack of dashboard voice calls, sms, network selection and ussd facility is not being used for which every time I have to open windows in virtual box.
Is it possible to get huawei dashboard in ubuntu? If yes how? And if no how can I avail voice call and ussd facility in ubuntu using my huawei 3g data card?
Plz help friends!

---

### Post by gandaran on 2012-09-01
I have never used the mobile partner software but if this software has a gui you can open the program using terminal just by typing the name, also did you type the name in the Ubuntu side bar dash?
another way is to explore the installed software directory and look for a start icon.
sorry I cant help with the other questions.

edit.
I have installed the Mobile Partner software, I was just curious if it would work with my E169g modem and it does very well but takes about three minutes for the software to open after plugging the modem in and I had to remove the network manager mobile setup to avoid conflicts. 
And yes there is a start icon for mobile partner in the applications menu, from the dash just type mobile partner.

---

### Post by celebratinglife on 2012-09-10
> **gandaran said:**
> I have never used the mobile partner software but if this software has a gui you can open the program using terminal just by typing the name, also did you type the name in the Ubuntu side bar dash?
another way is to explore the installed software directory and look for a start icon.
sorry I cant help with the other questions.

edit.
I have installed the Mobile Partner software, I was just curious if it would work with my E169g modem and it does very well but takes about three minutes for the software to open after plugging the modem in and I had to remove the network manager mobile setup to avoid conflicts. 
And yes there is a start icon for mobile partner in the applications menu, from the dash just type mobile partner.

thanks 4reply! I got that mobile partner icon and application works very well but it doesnt have options for voice call and ussd.
Does ur mobile partner version support voice call and ussd?

---

### Post by greattime on 2012-12-29
Hi celebratinglife can you please explain the procedure you did for installing huawei E303C, i have bought the same datacard about a week ago but was not able to make it work on my ubuntu 10.04. Can you please explain what all dependencies are needed to install it, and i am getting error using sakis3g, done lot of things like using modswitch etc, and searching net a lot for this model and at last i found this thread, hope you can help me, can you explain step by step how you configured and installed your modem(huawei E303c) in ubuntu 10.04.

---

### Post by celebratinglife on 2012-12-30
> **greattime said:**
> Hi celebratinglife can you please explain the procedure you did for installing huawei E303C, i have bought the same datacard about a week ago but was not able to make it work on my ubuntu 10.04. Can you please explain what all dependencies are needed to install it, and i am getting error using sakis3g, done lot of things like using modswitch etc, and searching net a lot for this model and at last i found this thread, hope you can help me, can you explain step by step how you configured and installed your modem(huawei E303c) in ubuntu 10.04.

hi! Sakis 3g works like a charm but if u have already installed mobile partner, then sakis 3g wont work. Does the huawei mobile partner dashboard auto launch when u insert the device? Does it autolaunch when u start the system? If yes what error it shows?
I advise u to upgrade ur system to 12.04 Lts. Do a fresh install if possible. Huawei devices work without any software in precise.

---

### Post by greattime on 2012-12-30
hi but i have made a lot of settings in the 10.04 system, so i cant just install a fresh copy again. And also i have found that the linux driver given with my modem was corrupted, so i downloaded the latest version of the driver from huaweidevice website ,
version 4.19.19.00 and run it so now i was able to run the driver, previously even that was not possible, and installed but with lot of errors,still can"t connect to internet using it. I am posting the result here, check can you help me from it.

[COLOR=Indigo]DRIVER COPY START
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
qmi_wwan interface not exist,ok[/COLOR]

---

### Post by celebratinglife on 2012-12-31
Hi!
are u getting the mobile partner icon in app menu???
if yes what u get when u launch the mobile partner app by clicking its icon? Actually i am on a trip with my lappy running Precise...so cnt help u much at present as i cnt access my 10.04 system. 
I too installed a version other than that  provided in the datacard. Try to search for higher version. As far as i remember version 4.20 or 4.21 (nt official one) worked for me bt i am nt so sure abt the version no. and cnt tell u exactly till i return back! Till then try googling.
One more thing in my lucid system i have to launch sakis 3g to make the device discoverable in mobile partner!

---

### Post by juempoes on 2013-01-03
I was searching and searching the way to fix my network connection and finally i did it. It works without any command on terminal. The software is included in that version. I don't know if that "fix" works with 12.04 of later, but it's not bad idea to prove.

You must change it in dashhome>Disks

there will appear

(1) CD Drive Huawei Mass Storage

and (2) Drive Huawei SD Storage

Inside settings (edit mount options)

to you must change in (1)

mount point: /mnt/usb-HUAWEI_Mass_Storage-0:0

to

mount point: /dev/sr0

choice

Identify As: /dev/disk/by-id/usb-HUAWEI_Storage-0:0

***and in (2)

choice

mount point: /mnt/pci-0000:00:14.0-usb-0:1:1.5-scsi-0:0:0:0

identify as: /dev/disk/by-path/pci-0000:00:14.0-usb-0:1:1.5-scsi-0:0:0:0

---

### Post by pabitra on 2013-02-01
> **juempoes said:**
> I was searching and searching the way to fix my network connection and finally i did it. It works without any command on terminal. The software is included in that version. I don't know if that "fix" works with 12.04 of later, but it's not bad idea to prove.

You must change it in dashhome>Disks

there will appear

(1) CD Drive Huawei Mass Storage

and (2) Drive Huawei SD Storage

Inside settings (edit mount options)

to you must change in (1)

mount point: /mnt/usb-HUAWEI_Mass_Storage-0:0

to

mount point: /dev/sr0

choice

Identify As: /dev/disk/by-id/usb-HUAWEI_Storage-0:0

***and in (2)

choice

mount point: /mnt/pci-0000:00:14.0-usb-0:1:1.5-scsi-0:0:0:0

identify as: /dev/disk/by-path/pci-0000:00:14.0-usb-0:1:1.5-scsi-0:0:0:0i followed the process.. but theres comes a pop up saying error mounting.. :(

---

