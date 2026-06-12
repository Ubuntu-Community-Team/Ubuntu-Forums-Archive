---
title: "Problem with virtual box"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by rraj.be on 2008-06-03
when i started my virtual box to install any OS its dieplaying this error message

```

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
```

what should i do?

---

### Post by hyper_ch on 2008-06-03
I'd say load the vboxdrv kernel module
```

sudo depmod vboxdrv

```

---

### Post by prshah on 2008-06-03
> **rraj.be said:**
> when i started my virtual box to install any OS its dieplaying this error message

```

install the virtualbox-ose-modules package for your kernel and execute  
```

what should i do?

Close Virtual Box, Open a terminal (Applications-Accessories-Terminal), then give the following commands 
```
sudo apt-get install virtualbox-ose-modules-generic
```

Then try running virtual box again.

---

### Post by marks_linux on 2008-06-03
I just did the:

sudo /etc/init.d/vboxdrv start

I think it was the last lot of updates (or the kernel update) that knocked it. All is well after running that command.

---

### Post by rraj.be on 2008-06-03
i have already installed my kernal image.

when i tried to load that it displayed

```
raj@raj-workstation:~$ sudo depmod vboxdrv
[sudo] password for raj: 
WARNING: Can't read module vboxdrv: No such file or directory
raj@raj-workstation:~$ 

```

whats the problem when i had already installed that required package but i cant find that in any folders

---

### Post by horgi on 2008-06-03
> **marks_linux said:**
> I just did the:

sudo /etc/init.d/vboxdrv start

I think it was the last lot of updates (or the kernel update) that knocked it. All is well after running that command.

-desktop:~$ sudo /etc/init.d/vboxdrv start
 * Starting VirtualBox kernel module                                            
 * No suitable module for running kernel found
-desktop:~$ 

it wasn't working for me. Any ideas?

---

### Post by rraj.be on 2008-06-03
This one solved my problem.

You have to install

```
virtualbox-ose-modules-generic
```

You can find packages in synaptic package manager.
But there is no need to install all.

you should install according to your kernal version.

If you are using 2.6.24-16-generic

then you should install

 ```
virtualbox-ose module for linux-image-2.6.24-16-generic

```

use this code to install

```
 sudo apt-get install virtualbox-ose module for linux-image-2.6.24-16-generic

```

Then before starting you should add yourself to vbox user group .

to add enter the code below.

```
sudo adduser <username> vboxusers
```

Now you need to Log out and login to add your self to that group succesfully.

Now you can use virtual box.

---

### Post by prshah on 2008-06-03
> **rraj.be said:**
> This one solved my problem.
You have to install
```
virtualbox-ose-modules-generic
```

If you are using 2.6.24-16-generic

then you should install

 ```
virtualbox-ose module for linux-image-2.6.24-16-generic

```


"virtualbox-ose-modules-generic" is a meta-package which will automatically select the correct version for your current kernel. 

There is no need to specify your kernel version if you are using the command in post #3.

---

### Post by rraj.be on 2008-06-03
Yes this too will help you.

But for a Newbie its recommended to use synaptic package manager than using command line as they are not experienced with that a lot.

So only i had pointed both the options.

But for other go your idea will be the best.

---

