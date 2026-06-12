---
title: "I lost the boots windows and ubuntu"
date: 2017-01-01
forum: New to Ubuntu
---

### Post by rezapci on 2017-01-01
Hello

I have a problem that when i install the ubuntu in my laptop with windows 10pro i lost the windows boot, then when i went to fix that i lost both now windows boot and ubuntu boot, now I am on live session with ubuntu ... i did tried everything didn't work...and here is the report [http://paste2.org/BK3DjDYb](http://paste2.org/BK3DjDYb)

---

### Post by Keith_Helms on 2017-01-01
I suspect you did something like installed Ubuntu in non UEFI mode on a UEFI system.  From the report you pasted, it looks like windows and ubuntu are still intact on the hard drive, so I wouldn't do anything else to the system until somebody with advanced install knowledge shows up to help.

---

### Post by yancek on 2017-01-01
At the bottom of the boot repair output, it tells you that you are running it's session in 'Legacy' mode and to run it in EFI mode.  Give that a try.
You have windows code in the MBR of your drive.  Is this an upgrade from a windows 7 system which was using the MBR method to boot?  You also have an EFI partition with boot files for both windows and Ubuntu so you need to make sure the computer is set to boot in EFI mode in the BIOS.  Your system is using GPT partitioning so windows requires it be EFI.

---

