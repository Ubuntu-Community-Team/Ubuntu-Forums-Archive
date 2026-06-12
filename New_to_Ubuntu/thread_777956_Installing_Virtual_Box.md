---
title: "Installing Virtual Box"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by JoyceBabu on 2008-05-01
I want to install Virtual Box. Can someone plz tell me which all packages I have to install. I have installed just virtualbox-ose. But when I try to install Windows XP, I am getting the error that kernal is not installed.

---

### Post by robalcorn on 2008-05-01
Not sure if this will help but someone gave me this link and everything works.

[http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html)


Also using virtualbox ose you don't get usb support so In my opinion its better to download from there site directly.

---

### Post by Monicker on 2008-05-01
> **JoyceBabu said:**
> I want to install Virtual Box. Can someone plz tell me which all packages I have to install. I have installed just virtualbox-ose. But when I try to install Windows XP, I am getting the error that kernal is not installed.

You also need to install the kernel module.  

Most likely it will be this package:

```
virtualbox-ose-modules-2.6.24-16-generic
```


From a terminal, run this command, to verify your kernel version:

```
uname -a
```


The kernel module should be listed in Synaptic, you can install from the terminal also
```

sudo apt-get install virtualbox-ose-modules-2.6.24-16-generic
```

---

### Post by JoyceBabu on 2008-05-01
> **robalcorn said:**
> Not sure if this will help but someone gave me this link and everything works.

[http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html)


Also using virtualbox ose you don't get usb support so In my opinion its better to download from there site directly.
I tried that and got the same error message on creating a virtual machine for XP :(

Let me try the second method

---

### Post by JoyceBabu on 2008-05-01
Oops! My wrong. I read 'accessible' as 'available'. :oops:
> 
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 

---

### Post by Monicker on 2008-05-01
> **JoyceBabu said:**
> Oops! My wrong. I read 'accessible' as 'available'. :oops:

Okay.  I have seen this before.  It doesnt look like the virtualbox driver got loaded.

Check in /etc/init.d for a vbox  or virtualbox file; I don't recall the exact name off the top of my head.

If its there do 

```
/etc/init.d/virtualbox start
update-rc.d virtualbox defaults
```

After that check to see if the driver is loaded

```
lsmod | grep vboxdrv
```

---

### Post by Monicker on 2008-05-01
Blah.  I am blind today.  The error message is clear.  I just need to read the whole thing.  :P

Add yourself to the vboxusers group.

System -> Administration -> Users and Groups

Unlock it, then select Manage Groups

Then you can add yourself to the vboxusers group.

---

### Post by JoyceBabu on 2008-05-01
I added current user to the group and restarted the system and now it is working fine.

Thanks a lot for all the help. I like this community :)

---

