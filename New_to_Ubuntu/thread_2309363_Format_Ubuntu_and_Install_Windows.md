---
title: "Format Ubuntu and Install Windows"
date: 2016-01-09
forum: New to Ubuntu
---

### Post by Axesh_Ajmera on 2016-01-09
Hi,

I recently installed ubuntu and want to go back to windows, but I could not boot from USB. I cannot use a live CD since my CD-Rom is not working, so the only option is via USB.

I do not want to do dual boot either. Any guide on how I can completely format ubuntu from my hard disk and install windows.

---

### Post by sandyd on 2016-01-09
What issues are you having booting from USB?

To go back to Windows, you will first need to create a Linux LiveUSB. See the instructions here [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu).

Go to gparted, and make sure that the correct drive is selected on the top-right hand corner dropdown. Delete all the partitions as well as extended partitions.

You can then use [Rufus]("https://rufus.akeo.ie/") to create a bootable Windows USB drive as long as you have the Windows installation media.

Rufus will require another Windows computer to run.

---

### Post by leunam12 on 2016-01-09
[FONT=arial]What happens when you try to boot from USB? Have you tried going to BIOS and enabling legacy mode? Is the distribution on the USB 64 bit and the computer 32 bit? A little more information is required for any one to help you with this issue.

There are other alternatives that may boot easier: Download Gparted and burn to USB[/FONT] and boot from it and create a new partition table (MBR or GPT depending on what version of Windows and what computer). Other options are Minitool Partition Wizard, Knoppix, Parted Magic, etc.When you have created the new partition table boot your Windows Installation Media and choose install and create a new partition there. Windows installer will create other partitions that are necessary.

---

### Post by Vladlenin5000 on 2016-01-10
> **sandyd said:**
> To go back to Windows, you will first need to create a Linux LiveUSB. See the instructions here [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu).

Go to gparted, and make sure that the correct drive is selected on the top-right hand corner dropdown. Delete all the partitions as well as extended partitions.

No, you don't. The Windows installer is self-sufficient for that task. Likewise. you wouldn't need to run or boot from Windows tools in order to delete or manage Windows partitions if your intention is to simply remove them in order to install a different OS.

And +1 to your first question... The inability to boot from the installation media has _absolutely nothing_ to do with what is or isn't installed already.

---

