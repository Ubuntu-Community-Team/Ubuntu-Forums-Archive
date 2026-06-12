---
title: "VirtualBox Kernel Driver"
date: 2013-04-26
forum: New to Ubuntu
---

### Post by Habanero101 on 2013-04-26
[SIZE=3]Hello,

While trying to use VirtualBox for the first time, I'm experiencing some errors, can you help me? Here's the details;
[/SIZE]

**[COLOR=#000080]Error 1[/COLOR]**
Kernel driver not installed (rc=-1908)


The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing


'/etc/init.d/vboxdrv setup'


as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.




**[COLOR=#000080]Error 2[/COLOR]**
Failed to open a session for the virtual machine Windows XP 32-bit.
The virtual machine 'Windows XP 32-bit' has terminated unexpectedly during startup with exit code 1.


**[COLOR=#000080]Terminal[/COLOR]**
User:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for user: 
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules                       [ OK ] 
 * Trying to register the VirtualBox kernel modules using DKMS                  Error! Your kernel headers for kernel 3.8.0-19-generic cannot be found.
Please install the linux-headers-3.8.0-19-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located


 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                        
 * Look at /var/log/vbox-install.log to find out what went wrong
User:~$ 




**[COLOR=#000080]/var/log/vbox-install.log[/COLOR]**
Uninstalling modules from DKMS
  removing old DKMS module vboxhost version  4.2.12


------------------------------
Deleting module version: 4.2.12
completely from the DKMS tree.
------------------------------
Done.
Attempting to install using DKMS


Creating symlink /var/lib/dkms/vboxhost/4.2.12/source ->
                 /usr/src/vboxhost-4.2.12


DKMS: add completed.
Failed to install using DKMS, attempting to install without
[B]Makefile:181: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.



[/B][COLOR=#000080]I believe this last bolded part holds the solution, but it's too much for me to make sense of right now. Can someone more knowledgeable give me a hand?[/COLOR]

---

### Post by CharlesA on 2013-04-26
Run this:

```
sudo apt-get install  linux-headers-3.8.0-19-generic
```

---

### Post by Habanero101 on 2013-04-27
> **Habanero101 said:**
> 

**[COLOR=#000080]Terminal[/COLOR]**
User:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for user: 
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules                       [ OK ] 
 * Trying to register the VirtualBox kernel modules using DKMS                  Error! Your kernel headers for kernel 3.8.0-19-generic cannot be found.
**[COLOR=#ff0000]Please install the linux-headers-3.8.0-19-generic package,[/COLOR]**
or use the --kernelsourcedir option to tell DKMS where it's located


 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                        
 * Look at /var/log/vbox-install.log to find out what went wrong
User:~$ 


> **CharlesA said:**
> Run this:

```
sudo apt-get install  linux-headers-3.8.0-19-generic
```
I can't believe the answer was right there all along.

Thanks for pointing that out.

I really got to pay more attention to those things.:p

---

