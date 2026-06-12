---
title: "Start ubuntu auto run workstation+load vm"
date: 2012-06-01
forum: New to Ubuntu
---

### Post by ldewittleedy on 2012-06-01
Lets start by saying this i have a pc with a Host OS of Ubuntu 12.04. I've installed VMware Workstation on it, and i put windows 7 as a virtual machine inside workstation.
 
My question is there a way to press the power button and as it loads up ubuntu(autologon) to have Vmware workstation auto start up then auto start my windows 7 virtual machine to full screen.(i already have it set to when i power on the windows 7 VM that it full screens.)
 
Thanks in advance. :)

---

### Post by Cheesemill on 2012-06-01
You can use the vmrun command to power on a VM, just add this to your startup applications so that it runs when you log on.

I don't have VMware Workstation on the machine I'm on at the moment but
```
man vmrun
```
should give you the correct syntax to start your VM.

---

### Post by ldewittleedy on 2012-06-01
Alright im somewhat understanding the syntex of the command, im putting this into "startup programs"
 
/usr/bin/vmrun /home/Administrator/vmware/""windows 7 x64""
 
and isnt working right. i tryed it in terminal also tells me "error: cannot open VM:/home/Administrator/vmware/windows 7 x64, unknown file suffix"

---

### Post by ldewittleedy on 2012-06-01
figured it out:

```
/usr/bin/vmrun start /home/administrator/vmware/"Windows 7 x64"/Windows7x64.vmx
```

---

### Post by Cheesemill on 2012-06-01
You need to call the full path to the .vmx file, for example:
```
vmrun start /home/administrator/vmware/Windows7/Windows7.vmx
```Edit - You beat me to it :)

---

### Post by ldewittleedy on 2012-06-01
:D thanks for the help

---

