---
title: "Bash script syntax error"
date: 2009-01-14
forum: Programming Talk
---

### Post by oygle on 2009-01-14
I'm trying to run a bash script to install a LAN driver for an ASUS mobo. I run the script, and get this error

> ./install.sh: 59: Syntax error: "(" unexpected

Here are the first 60 lines of the script, lines 1 to 58 are all comments, and line 59 is a function

```
#!/bin/sh
###############################################################################
# Part of Marvell Yukon/SysKonnect sk98lin Driver for Linux                   #
###############################################################################
# Installation script for Marvell Chip based Ethernet Gigabit Cards           #
# $Revision: 1.28 $                                                            #
# $Date: 2004/06/11 12:25:47 $                                                #
# =========================================================================== #
#                                                                             #
#  Main - Global function                                                     #
#                                                                             #
# Description:                                                                #
#  This file includes all functions and parts of the script                   #
#                                                                             #
# Returns:                                                                    #
#       N/A                                                                   #
# =========================================================================== #
# Usage:                                                                      #
#     ./install.sh                                                            #
#                                                                             #
# =========================================================================== #
# COPYRIGHT NOTICE :                                                          #
#                                                                             #
# (C)Copyright 2003-2004 Marvell(R).                                          #
#                                                                             #
#  This program is free software; you can redistribute it                     # 
#  and/or modify it under the terms of the GNU General Public                 #
#  License as published by the Free Software Foundation; either               #
#  version 2 of the License, or (at your option) any later version.           #
#                                                                             #
#                                                                             #
# WARRANTY DISCLAIMER:                                                        #
#                                                                             #
# THIS PROGRAM IS DISTRIBUTED IN THE HOPE THAT IT WILL BE USEFUL, BUT WITHOUT #
# ANY WARRANTY; WITHOUT EVEN THE IMPLIED WARRANTY OF MERCHANTABILITY OR       #
# FITNESS FOR A PARTICULAR PURPOSE.                                           #
#                                                                             #
# =========================================================================== #
#                                                                             #
#     History:                                                                #
#     2004-04-26    Version 2.02 - New parameter configuration    (mlindner)  #
#     2004-04-26    Version 2.01 - Support for Intel x86_64 arch  (mlindner)  #
#     2004-02-15    Version 2.00 - Support for yukon2 chipsets    (mlindner)  #
#                                  Support for kernel 2.6                     #
#                                  Support for parallel make on SMP-Hosts     #
#                                  Make a patch against the current kernel    #
#                                  Added help option.                         #
#                                  More command line parameters for auto inst.#
#                                  Better SMP detection                       #
#                                  Highmem detection                          #
#                                                                             #
#                                                                             #
###############################################################################


# Functions
###########################################

function message_status ()
{
```

Now I don't know much about bash scripts, but surely hitting a function before it is 'called' is maybe why it fell over ??

I see right down the bottom of the script is this 

```

# Start
#####################################################################

drv_name=`echo sk98lin`
#drv_name=`echo sk98lin`
working_dir=`pwd`
logfile="$working_dir/install.log"
rm -rf $logfile &> /dev/null
trap cleanup_trap INT TERM
KERNEL_TREE_MAKE=0;
VERSION="2.02 (20040608)"
clear

# Run main function
main_global $*

# Exit
exit 0
```

The 'start' is at the end, and the function 'main_global' is contained in the rest of the code.

Obviously I need to tell bash/sh to not execute those functions at the start, and drop down to the very end of the code,... where it all starts.

Oygle

---

### Post by oygle on 2009-01-14
I see from [here]("http://tldp.org/LDP/abs/html/functions.html") , that the structure of the function command should be ..

```
function function_name {
command...
}
or

function_name () {
command...
} 
```

so the script will have to be modified. Possibly as it was written in 2004, things have changed with bash script syntax since then ?

Oygle

---

### Post by Martin Witte on 2009-01-14
The script has as first line 
```
#!/bin/sh
```
which makes it a shell script, and not a bash script. in shell only the second form oygle describes is a valid function. As an alternative you can change the first line of the script to 
```
#!/bin/bash
``` and see if that works

---

### Post by oygle on 2009-01-15
Thanks Martin Witte, changing that first line did the trick. Ran the script, some permission errors, then ran it as 'sudo' and it _nearly_ completed.

> $ sudo ./install.sh

Installation script for sk98lin driver.
Version 2.02 (20040608)
(C)Copyright 2003-2004 Marvell(R).
====================================================
Add to your trouble-report the logfile install.log
which is located in the  DriverInstall directory.
====================================================

1) user installation	3) generate patch
2) expert installation	4) exit
Choose your favorite installation method: 1

Please read this carfully!

This script will automatically compile and load the sk98lin
driver on your host system. Before performing both compilation
and loading, it is necessary to shutdown any device using the
sk98lin kernel module and to unload the old sk98lin kernel 
module. This script will do this automatically per default.
If you want to shutdown and unload the old sk98lin kernel module
manually, run the script in the EXPERT mode.
 
Please plug a card into your machine. Without a card we aren't
able to check the full driver functionality.

Do you want proceed? (y/N) y

Create tmp dir (/tmp/Sk98IWjSITLUBiObeUjOPhUKJ)                                                                               [   OK   ]
Check user id (0)                                                                                                             [   OK   ]
Check kernel version (2.6.27-9-generic)                                                                                       [   OK   ]
Check kernel symbol file (/proc/kallsyms)                                                                                     [   OK   ]
Check kernel type (SMP)                                                                                                       [   OK   ]
Check number of CPUs (2)                                                                                                      [   OK   ]
Check architecture./install.sh: line 404: arch: command not found
 (found)                                                                                                                      [   OK   ]
Set architecture (i386)                                                                                                       [   OK   ]
Check compiler (/usr/bin/gcc)                                                                                                 [   OK   ]
Check mcmodel flags (32bit)                                                                                                   [   OK   ]
Check module support (/sbin/insmod)                                                                                           [   OK   ]
Check make (/usr/bin/make)                                                                                                    [   OK   ]
Check archive file (sk98lin)                                                                                                  [   OK   ]
Check kernel gcc version (4.3.2) (Kernel:4.3.2 == gcc:4.3.2)                                                                  [   OK   ]
Check sk98lin driver availability (not loaded)                                                                                [   OK   ]
Check kernel header files (not found)                                                                                         [ [COLOR="Red"]**failed**[/COLOR] ]
Kernel header not found. Please install the linux header files 
development package or crate a symbolic link from the 
/usr/src/KERNEL_VERSION directory to linux
     Example: ln -s /usr/src/KERNEL_VERSION /usr/src/linux

Installation of sk98lin driver module failed.
Delete temp directories (done)                                                                                                [   OK   ]
$

under the path where they sugest to add a symlink ..

> $ ls -al /usr/src
total 44
drwxrwsr-x 11 root src  4096 2008-12-19 22:48 .
drwxr-xr-x 13 root root 4096 2008-12-19 22:59 ..
drwxr-xr-x 20 root root 4096 2008-09-23 03:48 linux-headers-2.6.24-19
drwxr-xr-x  6 root root 4096 2008-09-23 03:48 linux-headers-2.6.24-19-generic
drwxr-xr-x 20 root root 4096 2008-11-26 16:10 linux-headers-2.6.24-21
drwxr-xr-x  6 root root 4096 2008-11-26 16:10 linux-headers-2.6.24-21-generic
drwxr-xr-x 20 root root 4096 2008-12-04 19:49 linux-headers-2.6.24-22
drwxr-xr-x  6 root root 4096 2008-12-04 19:50 linux-headers-2.6.24-22-generic
drwxr-xr-x 22 root root 4096 2008-12-19 22:48 linux-headers-2.6.27-9
drwxr-xr-x  7 root root 4096 2008-12-19 22:48 linux-headers-2.6.27-9-generic
drwxr-xr-x  2 root root 4096 2008-12-19 22:48 nvidia-173.14.12
$ 


No doubt I use the latest, but is it

```
ln -s /usr/src/linux-headers-2.6.27-9 /usr/src/linux
```

OR

```
ln -s /usr/src/linux-headers-2.6.27-9-generic /usr/src/linux
```

The install log shows

> +++ Install mode: User
+++ Kernel version 2.6.27-9-generic
+++ smp_count=1
+++ cpu_number=2
+++ kernel_machine=i686
+++ Architecture: i386
+++ Kernel header not found. ln -s /usr/src/KERNEL_VERSION?

so, it seems to have found the kernel, but not the kernel header. :confused:

Oygle

---

### Post by oygle on 2009-01-15
I tried this ..

```
$ symlinks -vr /usr/src

```

and there are a zillion symbolic links, but I have no idea which one it would be.

At the seventh post at [http://ubuntuforums.org/showthread.php?t=752977](http://ubuntuforums.org/showthread.php?t=752977) , this driver is meant to work out of the box. Also see [https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsMarvell](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsMarvell) and [https://bugs.launchpad.net/ubuntu/+bug/189982](https://bugs.launchpad.net/ubuntu/+bug/189982)

Later:  Hmm, maybe it does work out of the box, I can see this in /var/log/messages

> 
Jan 15 16:06:29  kernel: [    3.477646] sky2 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan 15 16:06:29  kernel: [    3.477705] sky2 0000:02:00.0: v1.22 addr 0xcdefc000 irq 17 Yukon-2 EC rev 1
Jan 15 16:06:29  kernel: [    3.478526] sky2 eth0: addr 00:00:00:00:00:00


(MAC address has been edited out).

Must be Marvell 88E8040 PCI-E Fast Ethernet Controller (rev 12)

I have been having major problems with network manager, in that it couldn't use ppp0 and eth0 at the same time, and eth0 is 'unmanaged', so I assume it's there and up (although no lights on).

Oygle

---

### Post by oygle on 2009-01-15
Don't know if this is a programming problem or a hardware/driver problem ? Seems a bit of both, please check [this thread]("http://ubuntuforums.org/showthread.php?t=1040738")

Oygle

---

