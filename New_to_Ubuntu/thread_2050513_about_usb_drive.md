---
title: "about usb drive"
date: 2012-08-31
forum: New to Ubuntu
---

### Post by navispidey on 2012-08-31
i am having error with my usb drive,when i connect usb drive and check on(devices-usb devices)i see my usb drive
but when i click on usb drive it shows error msg like this
failed to attach usb drive to vertual machine and this


Result Code: 
E_INVALIDARG (0x80070057)
Component: 
HostUSBDevice
Interface: 
IHostUSBDevice {173b4b44-d268-4334-a00d-b6521c9a740a}
Callee: 
IConsole {1968b7d3-e3bf-4ceb-99e0-cb7c913317bb}
help me please,i am beginner

---

### Post by lordievader on 2012-08-31
> **navispidey said:**
> failed to attach usb drive to vertual machine and this
Do you mean to say you are running a virtual machine? If so what is the host and the client (the OS run virtually)?
If you are using a virtual machine remember only one OS can use the usb-drive, so if the host has it mounted the client can not access it.

---

### Post by Hammer3344 on 2012-08-31
There are a couple of programs that you could install in order to help solve this issue. One of them being Pysdm```
sudo apt-get install psydm
```once the package has installed simply run ```
sudo psydm
```another program that I have used in conjunction with mount issues is NTFSfix
```
sudo apt-get install ntfsprogs
```
once the package is installed you can view the devices name by typing ```
sudo fdisk -l
```from the output you should see your device and then run
```
sudo ntfsfix /dev/(insert device)
```
 
Hopefully this helps in some way :)

---

### Post by navispidey on 2012-08-31
> **lordievader said:**
> Do you mean to say you are running a virtual machine? If so what is the host and the client (the OS run virtually)?
If you are using a virtual machine remember only one OS can use the usb-drive, so if the host has it mounted the client can not access it.

yes i am using vertual machine

---

### Post by navispidey on 2012-08-31
> **Hammer3344 said:**
> There are a couple of programs that you could install in order to help solve this issue. One of them being Pysdm```
sudo apt-get install psydm
```once the package has installed simply run ```
sudo psydm
```another program that I have used in conjunction with mount issues is NTFSfix
```
sudo apt-get install ntfsprogs
```
once the package is installed you can view the devices name by typing ```
sudo fdisk -l
```from the output you should see your device and then run
```
sudo ntfsfix /dev/(insert device)
```
 
Hopefully this helps in some way :)
i will try
thank you for reply

---

### Post by lordievader on 2012-08-31
> **navispidey said:**
> yes i am using vertual machine
Could you answer the other questions too. Is the host a Windows machine and the client a Linux (Ubuntu) machine?
Is the usb drive accessible from within the host, the one running the virtual machine?

---

### Post by navispidey on 2012-08-31
> **lordievader said:**
> Could you answer the other questions too. Is the host a Windows machine and the client a Linux (Ubuntu) machine?
Is the usb drive accessible from within the host, the one running the virtual machine?

yes i am running windows as host,i can access usb drive from windows but not with virtual machine

---

### Post by lordievader on 2012-08-31
> **navispidey said:**
> yes i am running windows as host,i can access usb drive from windows but not with virtual machine
Ok, what software are you using for the VM? (Virtual Box, VMware, etc)
In Windows try to safely remove the drive before letting the VM access it.

---

### Post by navispidey on 2012-09-01
> **lordievader said:**
> Ok, what software are you using for the VM? (Virtual Box, VMware, etc)
In Windows try to safely remove the drive before letting the VM access it.

i am using vertual box

---

### Post by lordievader on 2012-09-01
Ok, take a look at this guide, perhaps it will help you: [http://techtooltip.wordpress.com/2008/09/22/how-to-use-host-usb-device-from-guest-in-virtual-box/](http://techtooltip.wordpress.com/2008/09/22/how-to-use-host-usb-device-from-guest-in-virtual-box/)

---

### Post by navispidey on 2012-09-09
> **lordievader said:**
> Ok, take a look at this guide, perhaps it will help you: [http://techtooltip.wordpress.com/2008/09/22/how-to-use-host-usb-device-from-guest-in-virtual-box/](http://techtooltip.wordpress.com/2008/09/22/how-to-use-host-usb-device-from-guest-in-virtual-box/)
thank you very much:)
now everything working fine

---

### Post by lordievader on 2012-09-10
No problem, don't forget to mark this thread solved.

---

