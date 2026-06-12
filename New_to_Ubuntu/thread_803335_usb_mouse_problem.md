---
title: "usb mouse problem"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by valiexo on 2008-05-22
First of all, hello, I am glad for my presence here and sorry about my english!:lolflag:


I installed 8.04 ubuntu yesterday and I have a problem with my wheel microsoft mouse 1.1 (cable), when I boot ubuntu system does not regocnize my mouse, I have to unlugged it ande then plugged it again to work.

What I can do?
&#921; have 2 usb ports v1.


Thanks!:)

---

### Post by Biggy on 2008-05-22
unplugg and plugg again in another USB port your mouse and restart Ubuntu.
dulevi..

---

### Post by valiexo on 2008-05-22
I will try it... Thanks..

---

### Post by valiexo on 2008-05-22
Nope, didn't worked...

Every time I restart ubuntu I have to unplug and plug again in an other port my mouse.

Something else?

---

### Post by Biggy on 2008-05-22
in terminal type 
> lsusb

and post it here

---

### Post by valiexo on 2008-05-22
done
lsusb ->
> 

Bus 001 Device 018: ID 1110:9031 Analog Devices Canada, Ltd (Allied Telesyn) 
Bus 001 Device 015: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 014: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 001: ID 0000:0000  



I have 2 usb ports version 1
when I gave the lsub command, my mouse was in the one usb port
and there was a 4hub with my modem on it.

---

### Post by Biggy on 2008-05-22
terminal :
> sudo modprobe -r usbhid
sudo modprobe usbhid

---

### Post by valiexo on 2008-05-22
I will try it and soon i will post results.

---

### Post by valiexo on 2008-05-22
Nothing, I still have to unplug an plug again my mouse to my other usb port.

Why?

---

### Post by Biggy on 2008-05-22
u using desktop or laptop ?

try this command
> sudo dpkg-reconfigure xserver-xorg

---

### Post by valiexo on 2008-05-22
Desktop.

---

### Post by valiexo on 2008-05-22
I have tried...

Nothing at all!:confused:

---

### Post by Biggy on 2008-05-22
Well, the kernel is recognising the mouse. I would try unplugging then replugging the mouse back in (to a different port, if available) while Ubuntu is running.

---

### Post by valiexo on 2008-05-22
&#921; have done this to but again nothing...

---

### Post by Biggy on 2008-05-22
see USB options in BIOS

---

### Post by valiexo on 2008-05-22
All usb's options in BIOS are enabled.

---

### Post by Biggy on 2008-05-22
unplugg mouse from usb port restart ubuntu,replugg mouse and restart again

---

### Post by valiexo on 2008-05-22
Nothing, again...:(

---

### Post by valiexo on 2008-07-08
Problem solved, I bought a moder router by sweex and I have free one of the usb ports, system recognise mouse and also I have internet with my ubuntu at last.

Thank you all.

---

