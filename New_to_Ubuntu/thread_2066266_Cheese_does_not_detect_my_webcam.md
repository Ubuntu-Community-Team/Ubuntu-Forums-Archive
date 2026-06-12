---
title: "Cheese does not detect my webcam"
date: 2012-10-04
forum: New to Ubuntu
---

### Post by umesh314 on 2012-10-04
Hello all,

I am using 12.04 LTS, which i have installed recently.
When i try to run CHEESE camera application, it fails to detect my Webcam and display "No device found".

Need help.

---

### Post by GeForce 9500GT on 2012-10-04
Can you provide us with more info about your system and webcam?
And also do this:
 
- open a terminal
- type the following command:```
sudo lsusb
```
- place the output here

---

### Post by NikTh on 2012-10-04
Hi , 

First , place the results of command that [GeForce 9500GT ]("http://ubuntuforums.org/member.php?u=1694960")  suggested. 
Plus the result of 
```
lspci -nn
``` 

Also you can check the camera with this command 
```
gstreamer-properties
``` at the opened window goto Video => Output => click [Test] and any errors appeared in terminal copy-paste it here. 

Thanks


[]("http://ubuntuforums.org/member.php?u=1694960")

---

### Post by umesh314 on 2012-10-06
Hi. Thanks for your reply.

I have pasted the output of the commands mentioned.

umesh@ubuntu:~$ sudo lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
umesh@ubuntu:~$

umesh@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge [8086:7190] (rev 01)
00:01.0 PCI bridge [0604]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge [8086:7191] (rev 01)
00:07.0 ISA bridge [0601]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 08)
00:07.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:07.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 08)
00:07.7 System peripheral [0880]: VMware Virtual Machine Communication Interface [15ad:0740] (rev 10)
00:0f.0 VGA compatible controller [0300]: VMware SVGA II Adapter [15ad:0405]
00:10.0 SCSI storage controller [0100]: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI [1000:0030] (rev 01)
00:11.0 PCI bridge [0604]: VMware PCI bridge [15ad:0790] (rev 02)
00:15.0 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:15.1 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:15.2 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:15.3 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:15.4 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:15.5 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:15.6 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:15.7 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:16.0 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:16.1 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:16.2 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:16.3 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:16.4 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:16.5 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:16.6 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:16.7 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:17.0 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:17.1 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:17.2 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:17.3 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:17.4 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:17.5 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:17.6 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:17.7 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:18.0 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:18.1 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:18.2 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:18.3 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:18.4 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:18.5 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:18.6 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
00:18.7 PCI bridge [0604]: VMware PCI Express Root Port [15ad:07a0] (rev 01)
02:00.0 USB controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112]
02:01.0 Ethernet controller [0200]: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] [1022:2000] (rev 10)
02:02.0 Multimedia audio controller [0401]: Ensoniq ES1371 [AudioPCI-97] [1274:1371] (rev 02)
02:03.0 USB controller [0c03]: VMware USB2 EHCI Controller [15ad:0770]

---

### Post by GeForce 9500GT on 2012-10-06
> 
umesh@ubuntu:~$ sudo lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
umesh@ubuntu:~$
It looks like that Ubuntu doesn't recognize your wencam if this is the output of the command **sudo lsusb** of your system. You really don't have any other usb devices hooked up on your system?

What's the brand/model/type of your webcam?

---

### Post by Cheesemill on 2012-10-06
It looks like you are running Ubuntu in a VM.

If this is the case then your Ubuntu won't see any of your actual hardware until you make the appropriate settings in your VM host.

What software are you using for your VM's?

---

