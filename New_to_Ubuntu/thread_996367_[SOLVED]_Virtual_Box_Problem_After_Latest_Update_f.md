---
title: "[SOLVED] Virtual Box Problem After Latest Update for Intrepid"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by Noobuntu2008 on 2008-11-28
Upon starting up my Virtual Machine (Which I have been using to sync to my Ipod Touch very successfully) I receive these error messages in two different windows.


Virtual machine 'JCN9000' has terminated unexpectedly during startup.


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Machine
Interface: 
IMachine {1e509de4-d96c-4f44-8b94-860194f710ac}

and

VERR_VM_DRIVER_NOT_INSTALLED (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu or Fedora should install the DKMS package at first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

I think this has to do with some of the updates I recently added. 

As my name suggests I just got Ubuntu this year and, while learning quickly, am still unfamiliar with a lot of things. So a step-by-step solution would be the most helpful and most appreciated.

---

### Post by Rolcol on 2008-11-28
Did you install it from the Ubuntu Repsoitories or from the .deb available at [http://virtualbox.org/](http://virtualbox.org/) ?

You'll probably have to reinstall since it's missing the kernel module.

---

### Post by howefield on 2008-11-28
Install the dkms package from synaptic package manager and then the command  as per your post

sudo /etc/init.d/vboxdrv setup

Your updates most likely included a kernel update which has caused your issue.

---

### Post by Noobuntu2008 on 2008-11-29
> **howefield said:**
> Install the dkms package from synaptic package manager and then the command  as per your post

sudo /etc/init.d/vboxdrv setup

Your updates most likely included a kernel update which has caused your issue.

Thank you very much! That simple command made everything work again.

---

### Post by Orographic on 2009-01-28
And a thank you from me too. I had the same problem until I installed DKMS from synaptic and then entered that terminal command.

Ironically, the .deb file version 2.1.2 of Virtual Box has been running flawlessly so far compared to the repository version or the version 2.1.0 installed by doing this:

[http://www.ubuntugeek.com/how-to-install-virtualbox-21-in-ubuntu-810-intrepid-ibex804-hardy-heron.html](http://www.ubuntugeek.com/how-to-install-virtualbox-21-in-ubuntu-810-intrepid-ibex804-hardy-heron.html)


Maybe the 2.1.2 version resolved some of the kernel panic I had in 2.1.0, so I don't know if it was that or the fact that used the .deb file instead.

---

### Post by FiskFisk33 on 2009-02-03
my problem is very similar to the above but when i run the command i get 
```
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong

```

 and in the log mentioned above i find
```
Attempting to install using DKMS
  removing old DKMS module vboxdrv version 

Error! Invalid number of parameters passed.
Usage: remove -m <module> -v <module-version> --all
   or: remove -m <module> -v <module-version> -k <kernel-version>

------------------------------
Deleting module version: 2.1.2
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/2.1.2/source ->
                 /usr/src/vboxdrv-2.1.2

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.27-9-server cannot be found at
/lib/modules/2.6.27-9-server/build or /lib/modules/2.6.27-9-server/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:143: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
```

Any ideas?
(im running interpid btw)

---

### Post by northwestuntu on 2009-02-05
thanks from me too.  i wondered what had happened? but i just did updates and it stopped working.  your advice worked

---

