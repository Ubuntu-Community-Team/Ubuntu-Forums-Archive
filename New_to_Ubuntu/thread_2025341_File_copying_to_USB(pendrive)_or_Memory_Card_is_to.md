---
title: "File copying to USB(pendrive) or Memory Card is too slow"
date: 2012-07-14
forum: New to Ubuntu
---

### Post by macsathish on 2012-07-14
I'm using ubuntu 12.04 with gnome 3.4...i regulary update from update manager... my problem is when i copy file from hard disk to usb disk or memory card(mobile phone) file transfer is very slow... but at first when i installed ubuntu is normal speed but now it is very slow?i don't know wat's problem..pls help me.....

---

### Post by OM55 on 2012-07-14
Can you please clarify the following:

1. What is the speed you are getting now?

2. Do you have another USB disk/memory card you can try to copy to? (to confirm the problem is not specific to a certain USB disk)

3. What is the USB disk formatting type? (FAT32, NTFS etc.)

I suggest that for any copy speed test you always use a single large file, same file every time. If you copy many small files, the overhead will increase and the copy speed will decrease and will not be accurate as it will be affected by the number and size of files.

---

### Post by techvish81 on 2012-07-16
remove all other usb devices and keep just the pendrive and try copying the same file again. i got somewhat of a solution to this problem. i had a cheap chinese bluetooth dongle which was not usb 2.0. (even if it was depicted to be usb2.0) when it was inserted , all other ports become slow.

one more thing to check in the motherboard manual , some intel mobo's have special usb header for working with flashdrives to which the usb port is to be connected internally , to get maximum speed.

i also added pci=acpi in the grub config and added 

ehci_hcd
uhci_hcd 

in etc/initramfs-tools/modules but that did nothing. 

i know get near 7 mb/s speed after doing the first two workarounds and i think it is enough for me.

---

### Post by Kain000 on 2012-07-16
I agree, you should first test with only the pen drive in question connected, same file and compair.  You may want to look at the system monitor while doing this as something in the background may be taking up bandwidth on your southbridge chip (handles all of your computer's input output functions such as USB devices)

also I would go ahead and check the file system on your pen drive for errors

---

### Post by macsathish on 2012-07-22
In the beginning i get even more than 10mb/sec to 15 mb/sec, but now i only get 2mb/sec to 5mb/sec and also i checked with different usb drive, same slow speed i got, but i used the same usb drive in my friend system who uses windows 7 to copy same set of files which are 
copied for testing purpose. In windows 7 usb works faster, but in my system same usb drive with same set of files (yeah files are not small files they are videos in range > 700 mb) copies too slow
I already told that in beginning of OS installation,
i had no problem, but just two weeks before i got this problem
format for usb drive i use is FAT32

---

### Post by abybaddi on 2012-07-22
> **macsathish said:**
> In the beginning i get even more than 10mb/sec to 15 mb/sec, but now i only get 2mb/sec to 5mb/sec and also i checked with different usb drive, same slow speed i got, but i used the same usb drive in my friend system who uses windows 7 to copy same set of files which are 
copied for testing purpose. In windows 7 usb works faster, but in my system same usb drive with same set of files (yeah files are not small files they are videos in range > 700 mb) copies too slow
I already told that in beginning of OS installation,
i had no problem, but just two weeks before i got this problem
format for usb drive i use is FAT32

I've the same problem on my ubuntu as well as win7 ultimate. For large files the speed gradually drops and reduces to the order of Kb/s.

I would be glad if someone helped out.

---

### Post by techvish81 on 2012-07-22
if it happens in win7 also, have you checked with different pendrives with both OSs ? if it happens everytime,  we can derive that it is something related to hardware.

---

### Post by sudodus on 2012-07-22
I suggest that you try to test if it is a hardware or software problem.

1. Try with other USB ports.

2. Boot your computer from a CD or USB drive, and check the copying speed. If is is higher than with your installed system, then we can guess it is a software problem, otherwise it might be a hardware problem in your computer.

---

