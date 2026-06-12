---
title: "Installing .deb extensions."
date: 2011-11-11
forum: New to Ubuntu
---

### Post by Mikesla on 2011-11-11
The simple topic really doesn't cover what I am experiencing at the moment, and since I'm very new to this whole linux thing...well I dumbfounded to say the least.

 I have an internal modem, after downloading, and using a program called scanModem to find out what type of pci modem I have I downloaded I think the proper modem driver from "Linuxant" since my modem has Conexant internals which has the .deb extension.

There are several different types for different Linux os's. The one at the bottom has Ubuntu so thats the one I downloaded.

How do I install these modem drivers? I doubled clicked on the deb file, and the software center popped up, and it doesn't give me the option to install it. The install option is there just not able to select it (whited out).

I'm lost, any ideas?

Thank You.

---

### Post by Perfect Storm on 2011-11-11
There may different reason why you can't installed the .deb file.
Two commonly reason:
1) wrong architecture (32-bit or 64-bit)
2) Missing Dependencies  (The require libraries are not available through Ubuntu Software Center).


Try this,
Open the terminal;
write

sudo dpkg -i 

Then drag the .deb package into the terminal so it looks like something like this;
```
sudo dpkg -i /home/<username>/Downbloads/<package-name>.deb
```

hit <enter> key.
If you can please post the output of the terminal.

---

### Post by Mikesla on 2011-11-11
Thank you for responding so quickly. Also I forgot to tell you the version of Ubuntu I am running. Version 11.10.

 The command line you posted works, unfortunately I am running into a fatal error.

Here is the log...

> driver version 1.21full
(cd /lib/modules/3.0.0-12-generic/build && make "CNXT_KERNELSRC=/lib/modules/3.0.0-12-generic/build" "M=/usr/lib/hcfpcimodem/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/3.0.0-12-generic/build/.tmp_versions/hcfpciosspec.mod  /lib/modules/3.0.0-12-generic/build/.tmp_versions/hcfpciserial.mod  /lib/modules/3.0.0-12-generic/build/.tmp_versions/hcfpciengine.mod  /lib/modules/3.0.0-12-generic/build/.tmp_versions/hcfpcihw.mod Modules.symvers GPL/hda/Modules.symvers Module.symvers GPL/hda/Module.symvers modules.order GPL/hda/modules.order Module.markers GPL/hda/Module.markers
(cd /lib/modules/3.0.0-12-generic/build && make "CNXT_KERNELSRC=/lib/modules/3.0.0-12-generic/build" "M=/usr/lib/hcfpcimodem/modules" "CC=gcc" modules)
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  CC [M]  /usr/lib/hcfpcimodem/modules/mod_engine.o
  CC [M]  /usr/lib/hcfpcimodem/modules/mod_hcfpci.o
  CC [M]  /usr/lib/hcfpcimodem/modules/mod_osspec.o
In file included from /usr/lib/hcfpcimodem/modules/mod_osspec.c:323:0:
/usr/lib/hcfpcimodem/modules/imported/include/testdebug.h:181:2: warning: #warning FILEIDNUM not defined [-Wcpp]
In file included from /usr/lib/hcfpcimodem/modules/mod_osspec.c:323:0:
/usr/lib/hcfpcimodem/modules/imported/include/testdebug.h:181:2: warning: #warning FILEIDNUM not defined [-Wcpp]
  CC [M]  /usr/lib/hcfpcimodem/modules/osservices.o
In file included from /usr/lib/hcfpcimodem/modules/osservices.c:20:0:
/usr/lib/hcfpcimodem/modules/GPL/oscompat.h:201:57: error: 'SPIN_LOCK_UNLOCKED' undeclared here (not in a function)
In file included from /usr/lib/hcfpcimodem/modules/osservices.c:44:0:
/usr/lib/hcfpcimodem/modules/imported/include/testdebug.h:181:2: warning: #warning FILEIDNUM not defined [-Wcpp]
/usr/lib/hcfpcimodem/modules/osservices.c:51:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[2]: *** [/usr/lib/hcfpcimodem/modules/osservices.o] Error 1
make[1]: *** [_module_/usr/lib/hcfpcimodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make: *** [all] Error 2


Just to let you know this is the generic driver I downloaded because the first drivers were not designed for the kernel I am running.

---

### Post by Perfect Storm on 2011-11-11
Which modem model do you have? And computer specs in general.

---

### Post by Mikesla on 2011-11-11
> **Artificial Intelligence said:**
> Which modem model do you have? And computer specs in general.

My modem is a Supramax v.92 PCI (internal).

[Modem Info]
> For candidate card in slot 02:06.0, firmware information and bootup diagnostics are:
 PCI slot    PCI ID        SubsystemID    Name
 ----------    ---------    ---------    --------------
 02:06.0    14f1:1033    1092:0abf    Communication controller: Conexant Systems, Inc. HCF 56k Data/Fax Modem 

 Modem interrupt assignment and sharing: 
 --- Bootup diagnostics for card in PCI slot 02:06.0 ----
[    0.568102] pci 0000:02:06.0: [14f1:1033] type 0 class 0x000780
[    0.568125] pci 0000:02:06.0: reg 10: [mem 0xfebf0000-0xfebfffff]
[    0.568137] pci 0000:02:06.0: reg 14: [io  0xec00-0xec07]


[Computer Specs]
> Processor: AMD Phenom(tm) II X4 940 Processor (4 CPUs), ~3.0GHz
Memory: 4096MB RAM

Note: I have download what I think is the proper modem driver from [http://www.linuxant.com/drivers/hcf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hcf/full/downloads-ubuntu-x86.php). Unfortunately when trying to install it tells me this driver is not made for your version, or Kernel version.

Note 2: I then downloaded the generic version which starts up great but then gives me the fatal error when trying to install.

Thanks.

---

### Post by Perfect Storm on 2011-11-12
If you're using Ubuntu 11.10, you need to use this one: [http://www.linuxant.com/drivers/hcf/full/downloads.php#generic](http://www.linuxant.com/drivers/hcf/full/downloads.php#generic)
and compile the driver.
Ubuntu 11.10 uses kernel 3.0.x

---

### Post by Mikesla on 2011-11-13
> **Artificial Intelligence said:**
> If you're using Ubuntu 11.10, you need to use this one: [http://www.linuxant.com/drivers/hcf/full/downloads.php#generic](http://www.linuxant.com/drivers/hcf/full/downloads.php#generic)
and compile the driver.
Ubuntu 11.10 uses kernel 3.0.x


Thank You.

 Alright I just figured one of the bonehead mistakes I was making using make install.

Here is my problem now. Once the file is compiled, I them have to type in at the terminal prompt "hcfpciconfig"

It does whatever it is trying to do then I am presented with...

Where is the linux source build directory that matches your running kernel?
[/lib/modules/3.0.0-12-generic/build] "I'm not sure what it is asking me really so I just press enter"

Once I press enter I get this prompt error: ERROR: Module build failed!

Here is the log error...
> driver version 1.21full
(cd /lib/modules/3.0.0-12-generic/build && make "CNXT_KERNELSRC=/lib/modules/3.0.0-12-generic/build" "M=/usr/lib/hcfpcimodem/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/3.0.0-12-generic/build/.tmp_versions/hcfpciosspec.mod  /lib/modules/3.0.0-12-generic/build/.tmp_versions/hcfpciserial.mod  /lib/modules/3.0.0-12-generic/build/.tmp_versions/hcfpciengine.mod  /lib/modules/3.0.0-12-generic/build/.tmp_versions/hcfpcihw.mod Modules.symvers GPL/hda/Modules.symvers Module.symvers GPL/hda/Module.symvers modules.order GPL/hda/modules.order Module.markers GPL/hda/Module.markers
(cd /lib/modules/3.0.0-12-generic/build && make "CNXT_KERNELSRC=/lib/modules/3.0.0-12-generic/build" "M=/usr/lib/hcfpcimodem/modules" "CC=gcc" modules)
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  CC [M]  /usr/lib/hcfpcimodem/modules/mod_engine.o
  CC [M]  /usr/lib/hcfpcimodem/modules/mod_hcfpci.o
  CC [M]  /usr/lib/hcfpcimodem/modules/mod_osspec.o
In file included from /usr/lib/hcfpcimodem/modules/mod_osspec.c:323:0:
/usr/lib/hcfpcimodem/modules/imported/include/testdebug.h:181:2: warning: #warning FILEIDNUM not defined [-Wcpp]
In file included from /usr/lib/hcfpcimodem/modules/mod_osspec.c:323:0:
/usr/lib/hcfpcimodem/modules/imported/include/testdebug.h:181:2: warning: #warning FILEIDNUM not defined [-Wcpp]
  CC [M]  /usr/lib/hcfpcimodem/modules/osservices.o
In file included from /usr/lib/hcfpcimodem/modules/osservices.c:20:0:
/usr/lib/hcfpcimodem/modules/GPL/oscompat.h:201:57: error: &#8216;SPIN_LOCK_UNLOCKED&#8217; undeclared here (not in a function)
In file included from /usr/lib/hcfpcimodem/modules/osservices.c:44:0:
/usr/lib/hcfpcimodem/modules/imported/include/testdebug.h:181:2: warning: #warning FILEIDNUM not defined [-Wcpp]
/usr/lib/hcfpcimodem/modules/osservices.c:51:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[2]: *** [/usr/lib/hcfpcimodem/modules/osservices.o] Error 1
make[1]: *** [_module_/usr/lib/hcfpcimodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make: *** [all] Error


Again, thank you for taking the time.

---

