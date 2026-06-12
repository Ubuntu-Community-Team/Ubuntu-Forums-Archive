---
title: "Virtual box problems"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by keefy777 on 2008-07-20
Ok i have taken the plunge and reinstalled ubuntu as the system on my pc 
I have also installed Virtualbox and got it running 
I went through the wizard to set up a virtual pc and all seemed fine till i went to open the new system and i got this message


The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}



Any ideas i have not yet installed XP 
Your help as always is appreciated.

---

### Post by keefy777 on 2008-07-20
Forgot to add i have added myself as a user when i run the command in terminal it stated that user already there

---

### Post by asmoore82 on 2008-07-20
Add your user account to the vboxusers group...

Open "System -> Administration -> Users and Groups"

Unlock
Manage Groups
"vboxusers"
Properties

and as the error messages said, you will have to log out and back in for it to work

---

### Post by keefy777 on 2008-07-20
Ok i did that and now have this reply


The VirtualBox support driver which is running is from a different version of VirtualBox. You can correct this by stopping all running instances of VirtualBox and reinstalling the software..
VBox status code: -1912 (VERR_VM_DRIVER_VERSION_MISMATCH).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}


do i do "sudo apt replace virtualbox"

---

### Post by OldTimeTech on 2008-07-20
This is a how-to from one of the forum staff....it will help you to set up virtual box correctly!

[http://gaming.gwos.org/doku.php/udsf:virtualbox](http://gaming.gwos.org/doku.php/udsf:virtualbox)

Also, this is a question that should be asked in the virtualization forum here on Ubuntu....they are really great people to work with also ;)

---

### Post by asmoore82 on 2008-07-20
I would use Synaptic "System -> Administration -> Synaptic Package Manager"
to Reinstall VirtualBox **AND** the VirtualBox modules for your kernel verison

Then, this is the tricky part, you have to update the kernel's "map" of module dependencies...
in a terminal "Applications -> Accessories -> Terminal" run this
```
sudo depmod -v
```

I have noticed that Ubuntu's kernel updates always break VirtualBox OSE
as the virtualbox module update is always a couple days later.

I fix this by copying the vbox kernel module and running depmod, something like...
```
 sudo cp /lib/modules/2.6.24-18-generic/misc/vboxdrv.ko /lib/modules/2.6.24-19-generic/misc/vboxdrv.ko
sudo depmod -v
```
:|

---

