---
title: "How can I execute a command line in Ubuntu?"
date: 2014-08-10
forum: Philippine Team
---

### Post by commercial2 on 2014-08-10
Hi guys, I have a Ubuntu OS initially installed on my laptop but I also want to dual boot it with Windows 7.

I  managed to install a windows 7 installer on my USB using "Windows 7 USB  DVD Download Tool". However, I am getting a ntldr is missing as I boot  my usb on my laptop.

As I search from the internet, I found a quick fix on the following link
[http://chwang.blogspot.com/2012/07/fix-ntldr-is-missing-for-windows-78-usb.html](http://chwang.blogspot.com/2012/07/fix-ntldr-is-missing-for-windows-78-usb.html)


However, I don't know how to execute steps 3 & 4 because my os is Ubuntu.

Here is the excerpt of the steps from the link provided: 
> 
 
[LIST=1]
[*]Boot the existing windows (my one is XP, but windows 7 should also works)
[*]Insert the created windows 7/8 installer USB drive
[*]Open a command window, go to the USB drive (my one is G:) 
[*]Change directory to: USBDRIVE:\boot (for example, [FONT=Courier New]cd G:\boot[/FONT]) This directory contains the executable file "bootsect.exe". Under this directory, run the following command: 
[/LIST]
 
 [FONT=arial] [/FONT][FONT=Courier New]bootsect /nt60 **USBDRIVE**:  



can someone please help me?

Thanks!
[/FONT]

---

### Post by Elfy on 2014-08-10
Thread closed. Please do not post duplicates, it dilutes community effort.

---

