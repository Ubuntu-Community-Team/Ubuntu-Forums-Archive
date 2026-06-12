---
title: "vmserver on ubuntu linux 8.04 (problem)"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by mustimasti on 2008-07-14
After installating the vmserver i am trying to open from system tools but it doesnt work please help following are the log file

Do you accept? (yes/no) y

Thank you.

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-console-uri-handler.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-19-server/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.24-19-server/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-server'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmx86.o
/tmp/vmware-config0/vmmon-only/common/vmx86.c: In function ‘Vmx86_GetkHzEstimate’:
/tmp/vmware-config0/vmmon-only/common/vmx86.c:1899: warning: passing argument 4 of ‘Div643264’ from incompatible pointer type
/tmp/vmware-config0/vmmon-only/common/vmx86.c:1908: warning: passing argument 4 of ‘Div643232’ from incompatible pointer type
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-server'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
The module loads perfectly in the running kernel.

Do you want networking for your virtual machines? (yes/no/help) [yes] y

Configuring a bridged network for vmnet0.

The following bridged networks have been defined:

. vmnet0 is bridged to eth0

All your ethernet interfaces are already bridged.

Do you want to be able to use NAT networking in your virtual machines? (yes/no)
[yes] 

Configuring a NAT network for vmnet8.

Do you want this program to probe for an unused private subnet? (yes/no/help) 
[yes] 

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.137.0/255.255.255.0 appears to be unused.

The following NAT networks have been defined:

. vmnet8 is a NAT network on private subnet 172.16.137.0.

Do you wish to configure another NAT network? (yes/no) [no] n

Do you want to be able to use host-only networking in your virtual machines? 
[yes] 

Configuring a host-only network for vmnet1.

Do you want this program to probe for an unused private subnet? (yes/no/help) 
[yes] 

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.94.0/255.255.255.0 appears to be unused.

The following host-only networks have been defined:

. vmnet1 is a host-only network on private subnet 172.16.94.0.

Do you wish to configure another host-only network? (yes/no) [no] 

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.24-19-server/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-server'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config0/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_compat.o
  SHIPPED /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /tmp/vmware-config0/vmnet-only/.smac_linux.x386.o.cmd for /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-server'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
The module loads perfectly in the running kernel.

Please specify a port for remote console connections to use [902] 

 * Stopping internet superserver xinetd                                  [ OK ] 
 * Starting internet superserver xinetd                                  [ OK ] 
Configuring the VMware VmPerl Scripting API.

Building the VMware VmPerl Scripting API.

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Installing the VMware VmPerl Scripting API.

The installation of the VMware VmPerl Scripting API succeeded.

Generating SSL Server Certificate

In which directory do you want to keep your virtual machine files? 
[/var/lib/vmware/Virtual Machines] 

The path "/var/lib/vmware/Virtual Machines" does not exist currently. This 
program is going to create it, including needed parent directories. Is this 
what you want? [yes] 

Please enter your 20-character serial number.

Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel:  93M84-YRL86-24M94-4CNC5

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done

The configuration of VMware Server 1.0.6 build-91891 for Linux for this running
kernel completed successfully.

---

### Post by cdtech on 2008-07-14
Did you try the command line "vmware &" ?

---

### Post by mustimasti on 2008-07-14
hi i m new to linux and what comman should i run please tel me

---

