---
title: "How do you fix this?"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by winsane on 2008-08-26
I got a message during startup, it has red asterisk next to it..
No suitable module for kernel found
How do I troubleshoot this?

---

### Post by nicedude on 2008-08-26
This could be something you need to fix or it could be meaningless depending on what the error is in relation to. Do you know what device or software the error is in regards to? Is this a new install or has been working correctly until now? Is there anything broken with your system that you know of ( like sound or wifi etc )?

Please answer those and I or someone else reading can help more.

---

### Post by winsane on 2008-08-26
I never noticed it unitl I installed virtualbox, which doesn't work.
When I install virtualbox, it gives the same error.

---

### Post by winsane on 2008-08-26
It may not be important, but I can't play media in anything except Dragon Player.

---

### Post by winsane on 2008-08-26
Ok.. Let's see if this output helps anyone...

Unable to find a precompiled module for the current kernel!

Without a suitable kernel module you will never be able to start VMs. It is 
strongly recommended to compile a kernel module now. The kernel headers and the 
tools to build kernel modules (gcc, make, binutils, ...) are required. However, 
in case a suitable kernel module already exists at another place you might want 
to override the default position by setting KDIR=<full_path_to_vboxdrv_module> 
in /etc/default/virtualbox. The compilation can also be done later by executing

  /etc/init.d/vboxdrv setup

as root.

Should the vboxdrv kernel module be compiled now? yes


Messages emitted during module compilation will be logged to /var/log/vbox-install.log.
Compilation of the kernel module FAILED!

VirtualBox will not start until this problem is fixed. Please consult 
/var/log/vbox-install.log to find out why the kernel module does not compile. 
Most probably the kernel sources were not found. Install them and execute

  /etc/init.d/vboxdrv setup

as root.

 * Starting VirtualBox kernel module

 * No suitable module for running kernel found
 * Starting VirtualBox host networking
 *  done.

RESULT=0

So.....
I check out /var/log/vbox-install.log and here it is....

root@skinflint:/var/log# cat vbox-install.log
Makefile:127: *** Error: unable to find the sources of your current Linux kernel          . Specify KERN_DIR=<directory> and run Make again.  Stop.


What am I doing wrong here???

---

### Post by dondad on 2008-08-26
> **winsane said:**
> Ok.. Let's see if this output helps anyone...

Unable to find a precompiled module for the current kernel!

Without a suitable kernel module you will never be able to start VMs. It is 
strongly recommended to compile a kernel module now. The kernel headers and the 
tools to build kernel modules (gcc, make, binutils, ...) are required. However, 
in case a suitable kernel module already exists at another place you might want 
to override the default position by setting KDIR=<full_path_to_vboxdrv_module> 
in /etc/default/virtualbox. The compilation can also be done later by executing

  /etc/init.d/vboxdrv setup

as root.

Should the vboxdrv kernel module be compiled now? yes


Messages emitted during module compilation will be logged to /var/log/vbox-install.log.
Compilation of the kernel module FAILED!

VirtualBox will not start until this problem is fixed. Please consult 
/var/log/vbox-install.log to find out why the kernel module does not compile. 
Most probably the kernel sources were not found. Install them and execute

  /etc/init.d/vboxdrv setup

as root.

 * Starting VirtualBox kernel module

 * No suitable module for running kernel found
 * Starting VirtualBox host networking
 *  done.

RESULT=0

So.....
I check out /var/log/vbox-install.log and here it is....

root@skinflint:/var/log# cat vbox-install.log
Makefile:127: *** Error: unable to find the sources of your current Linux kernel          . Specify KERN_DIR=<directory> and run Make again.  Stop.


What am I doing wrong here???

Try looking in your sources list and make sure that the source code box is checked. If not, check it then look for updates. (it will probably do that when you close the box). Apply the updates and you should have the source. The kernel (and other) source downloads are not enabled by default as you won't need them unless you are going to compile something. It sounds like you don't have them on your system.

---

### Post by RequinB4 on 2008-08-26
try
```

sudo aptitude install virtualbox-ose-modules-`uname -r`

```

Assuming none of the above work, the files you need to compile might be in
```

sudo apt-get install kernel-package
sudo apt-get install linux-source

```

---

### Post by Separ on 2008-08-26
Check my post to another user with the same problem [Here]("http://ubuntuforums.org/showpost.php?p=5625289&postcount=4").

---

### Post by winsane on 2008-08-26
Ok. I checked off all the sources and ran synaptic install update.. No joy. Any thing else I'm missing?:confused:

---

### Post by winsane on 2008-08-26
Separ,
I cut and pasted your syntax directlyu to the command line and everything appeared to go okay but whe I run /etc/init.d/vboxdrv setup, I get errors...

---

### Post by jakupl on 2008-08-26
Just want to say that, for the future. It is better to have a title that properly describes your problem when posting new threads.
It makes it faster for you and everyone else.
Good luck and enjoy.

---

