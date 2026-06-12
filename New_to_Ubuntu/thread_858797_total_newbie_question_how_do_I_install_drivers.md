---
title: "total newbie question: how do I install drivers?"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by erans on 2008-07-13
I've been grappling with this network problem for a few days, and I'm pretty sure it's due to the drivers my network card is using. 

So I found some drivers that I want to install and try ([http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)).

Unfortunately, I have no idea how to install these drivers. I don't even know how to check to see if I have these drivers installed already by default. And (most importantly), if I manage to install these drivers and they don't work at all, I don't know how to roll back to the previous ones. 

Anyway, any advice for this problem would be much appreciated. I'm struggling.

edit: I dug around in the tar file and found a readme. Will these instructions translate to Ubuntu? 
```

* README

*

* Ralink Tech Inc.

*

* http://www.ralinktech.com

*



=======================================================================

ModelName:

===========

RT2500





=======================================================================

Supporting Kernel:

===================

linux kernel 2.4 and 2.6 series.

Tested in Redhat 7.3 or later, Fedora Core 1, Suse 8.0,8.1,9.0, Mandrake 9.0->10.0, Slackware 9.0,9.1







=======================================================================

Description:

=============

This is a linux device driver for Ralink RT2500 b/g WLAN Card.







=======================================================================

Contents:

=============

./2.4.x			: Makefile for kernel 2.4 series

./2.6.x			: Makefile for kernel 2.6 series

*.c			: c files

*.h			: header files

Makefile.BigEndian	: Makefile for big endian platform







=======================================================================

Features:

==========

   This driver implements basic IEEE802.11. Infrastructure and adhoc mode with open or shared or WPA

   authentication method. WEP-40 and WEP-104 TKIP and AES encryption,







=======================================================================

Build Instructions:

====================

For 2.4 series kernel:

a. $tar -xvzf RT2500-Linux-STA-x.x.x.x.tar.gz

    go to "./RT2500-Linux-STA-x.x.x.x/Module" directory.



b. Use 'chmod 755' command to change access right of following script files :

   'load', 'unload', 'Configure'



c. run 'cp ./2.4.x/Makefile .' and 'cp ./2.4.x/load .'



d. $make config         # config build linux os version



e. $make all            # compile driver source code



f. $load                # load/insmod module(rt2500.o)



Note: Script functionality:

load            load module to kernel

unload          unload module from kernel

Configure       retrieve linux version





For 2.6 series kernel:

a.  run 'cd STA/Module'

        'cp ./2.6.x/Makefile .'

        'cp ./2.6.x/load .'



b.  $make -C /path/to/source SUBDIRS=$PWD modules

    Where /path/to/source is the path to the source directory for the (configured and built) target kernel.



c.  run '/sbin/insmod rt2500.ko'  (as root)

        '/sbin/ifconfig ra0 inet YOUR_IP up'





For big endian platform:

a.  replace Makefile with Makefile.BigEndian







=======================================================================

To BUILD UTILITY

====================



a.  go to the "./Utility" directory



b.  run 'qmake -o Makefile raconfig2500.pro'

    If qmake command is not found in your system, you can download the QT tool

    'qt-x11-free-3.2.1' or later at

    http://www.trolltech.com/



    (qmake comes with RedHat 7.3 or later QT Package)



c.  run 'make" to compile the utility source code.



d.  After all, an execution file would be generated "RaConfig2500"

    run "RaConfig2500" to config the driver as you want







=======================================================================

CONFIGURATION:

====================

RT2500 driver can be configured via following interfaces,

i.e. (i)"iwconfig" command, (ii)"iwpriv" command, (iii) configuration file, (iv) RaConfig2500



i)  iwconfig comes with kernel.

ii) iwpriv usage, please refer to file "iwpriv_usage.txt" for details.

iii)copy configuration file "RT2500STA.dat" to /etc/Wireless/RT2500STA/RT2500STA.dat.

    Please refer to 3.1) for details.

iv) RT2500 provides API : RaConfig2500, please go to directory ./Utility and refer to how-to-compile.txt





Configuration File : RT2500STA.dat



# Copy this file to /etc/Wireless/RT2500STA/RT2500STA.dat

# This file is a binary file and will be read on loading rt2500.o module.

#

# Use "vi -b RT2500STA.dat" to modify settings according to your need.

#

# 1.) set NetworkType to "Adhoc" for using Adhoc-mode, otherwise using as Infrastructure-mode

# 2.) set Channel to "0" for auto-select on Infrastructure mode

# 3.) set SSID for connecting to your Accss-point.

# 4.) AuthMode can be "OPEN", "SHARED", "AUTO", "WPAPSK", "WPANONE"

# 5.) EncrypType can be "NONE", "WEP", "TKIP", "AES"

# for more information refer to the Readme file.

#

[Default]

CountryRegion=0

WirelessMode=0

SSID=AP350

NetworkType=Infra

Channel=0

AuthMode=OPEN

EncrypType=NONE

DefaultKeyID=1

Key1Type=0

Key1Str=0123456789

Key2Type=0

Key2Str=

Key3Type=0

Key3Str=

Key4Type=0

Key4Str=

WPAPSK=abcdefghijklmnopqrstuvwxyz

TXBurst=0

TurboRate=0

BGProtection=0

ShortSlot=0

TxRate=0

RTSThreshold=2312

FragThreshold=2312

PSMode=CAM

-----------------------------------------------

syntax is 'Param'='Value' and describes below.



1. CountryRegion=value

   value

        0:      for use channel 1-11

        1:      for use channel 1-11

        2:      for use channel 1-13

        3:      for use channel 10-11

        4:      for use channel 10-13

        5:      for use channel 14

        6:      for use channel 1-14

        7:      for use channel 3-9

2. WirelessMode=value

   value

        0:      802.11 B/G mixed

        1:      802.11 B only

3. SSID=value

   value

         1~32 ascii characters.

4. NetworkType=Infra

   value

       Infra : infrastructure mode

       Adhoc : adhoc mode

5. Channel=value

    value

        1~14 depends on  CountryRegion

6. AuthMode=value

    value

        OPEN      For Open System

        SHARED    For Shared key system

        AUTO

        WPAPSK

7. EncrypType=value

    value

        NONE      :For AuthMode=OPEN

        WEP       :For AuthMode=OPEN or AuthMode=SHARED

        TKIP      :For AuthMode=WPAPSK

        AES       :For AuthMode=WPAPSK

8. DefaultKeyID=value

    value

        1 ~ 4

9. Key1Type=value

    value

        0:        Hexadecimal

        1:        Ascii

10. Key1Str=value

    value

        10 or 26 hexadecimal characters eg: 012345678

        5 or 13 ascii characters eg: passd

11. Key2Type=value

    value

        0:        Hexadecimal

        1:        Ascii

12. Key2Str=value

    value

        10 or 26 hexadecimal characters eg: 012345678

        5 or 13 ascii characters eg: passd

13. Key3Type=value

    value

        0:        Hexadecimal

        1:        Ascii

14. Key3Str=value

    value

        10 or 26 hexadecimal characters eg: 012345678

        5 or 13 ascii characters eg: passd

15. Key4Type=value

    value

        0:        Hexadecimal

        1:        Ascii

16. Key4Str=value

    value

        10 or 26 hexadecimal characters eg: 012345678

        5 or 13 ascii characters eg: passd

17. WPAPSK=value

    value

        8 ~ 63 characters

          or

        64 hexadecimal characters

18. TxBurst=value

    value

        0:        Disable

        1:        Enable

19. TurboRate=value

    value

        0:        Disable

        1:        Enable

20. BGProtection=value

   value

        0:        Auto

        1:        Always On

        2:        Always Off

21. ShortSlot=value

    value

        0:        Disable

        1:        Enable

22. TxRate=value

   value

         0:     Auto

         1:     1 Mbps

         2:     2 Mbps

         3:     5.5 Mbps

         4:     11 Mbps

         5:     6  Mbps  //WirelessMode must be 0

         6:     9  Mbps  //WirelessMode must be 0

         7:     12 Mbps  //WirelessMode must be 0

         8:     18 Mbps  //WirelessMode must be 0

         9:     24 Mbps  //WirelessMode must be 0

        10:     36 Mbps  //WirelessMode must be 0

        11:     48 Mbps  //WirelessMode must be 0

        12:     54 Mbps  //WirelessMode must be 0

23. RTSThreshold=value

    value

        1 ~ 2312

24. FragThreshold=value

    value

        256 ~ 2312

25. PSMode=value

    value

    MAX_PSP   Power Saving Mode

    CAM   CAM (Constantly Awake Mode)



26. AdhocOfdm=value

    value

    0:		Adhere WIFI spec, the Tx MAX rate will be 11Mbps in Adhoc mode

    1:		Violate WIFI spec, the Tx MAX rate will be 54Mbps in Adhoc mode



27. StaWithEtherBridge=value

    value

    0:		Disable sta with ethernet to wireless bridge

    1:		Enable sta with ethernet to wireless bridge





MORE INFORMATION

=================================================================================

If you want for rt2500 driver to auto-load at boot time:

A) choose ra0 for first RT2500 WLAN card, ra1 for second RT2500 WLAN card, etc.



B) create(edit) 'ifcfg-ra0' file in /etc/sysconfig/network-scripts/,

   edit( or add the line) in /etc/modules.conf:

       alias ra0 rt2500



C) edit(create) the file /etc/sysconfig/network-scripts/ifcfg-ra0

   DEVICE='ra0'

   ONBOOT='yes'





NOTE:

   if you use dhcp, add this line too .

    BOOTPROTO='dhcp'



*D) To ease the Default Gateway setting,

    add the line

    GATEWAY=x.x.x.x

    in /etc/sysconfig/network





==================================================================================

= To install a device driver for Ralink RT2500 b/g WLAN card in AMD64 SUSE Linux =

==================================================================================

A.

1.Edit(or add the line) in /etc/modules.conf

   alias ra0 rt2500

2.Create and edit 'ifcfg-ra0' file in /etc/sysconfig/network/

   DEVICE='ra0'

   ONBOOT='yes'

   BOOTPROTO='dhcp'



B. $tar -xvzf RT2500--Linux-STA-x.x.x.x.tar.gz

   Go to "./RT2500-Linux-STA-x.x.x.x/Module" directory



1.Copy ./Module/2.6.x/Makefile to "./Module" directory

2.$make -C /usr/src/linux-2.6.8-gentoo-r3 SUBDIRS=$PWD modules

	where linux-2.6.8-gentoo-r3 is your 2.6 kernel name

3.$insmod rt2500.ko

4.$ifconfig ra0 up

5.$iwconfig ra0 essid any

6.$dhcpcd ra0&

7.$dhcpcd ra0



Now it should be functional - type

$iwconfig

to confirm setting



C.Activate it on startup with a script.

1.Input your script file 'wlancfg' in /etc/init.d/

2.Start applicaiton YaST in System, choose system -> runlevel editor

3.In expert mode, enable 'wlancfg' in runlevel 5.



```
Is this all that's needed to install the driver? If I need to roll back the driver, how would I do that (this part is not in the readme). Also, I don't know if I'm using a 2.4 kernel or 2.6 kernel. Very confused/intimidated.

---

### Post by deNoobius on 2008-07-13
Have you tried going to System/Administration/Hardware Drivers and seeing if your drivers are listed, and if so, whether the "enabled" box is checked?  If the driver is listed but the "enabled" box is not checked, check it and apply the change.  That should fix the problem.

---

### Post by erans on 2008-07-13
Yup, I checked that. It says "No proprietary drivers are in use on this system."

---

### Post by LeoSolaris on 2008-07-14
In theory it ***should*** work, but being able to undo it is a good idea. Your kernel if you're using Hardy 8.04.1 (completely updated) is 2.6.24-19

In theory what you're doing to rewriting the kernel, so to undo it, have a second, older kernel available to boot from. You can do that by picking one out of synaptic. The current one should be 2.6.24-19, so 2.6.24-18 should do fine. All you would have to do is boot from the 18 kernel, and use synaptic to remove the 19 kernel, then reinstall it. You may have a few stray unused configuration files left after that, but they shouldn't do anything. You could remove them if you're a tidy person.

Here is a site I find to be helpful in installing things. [->HERE<-]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by ProNux on 2008-10-12
type in the terminal:

uname -r

and press enter.  The kernel version you are using will be displayed.

---

