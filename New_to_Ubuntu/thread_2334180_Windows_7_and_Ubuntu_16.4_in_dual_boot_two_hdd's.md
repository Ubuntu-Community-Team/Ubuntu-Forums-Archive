---
title: "Windows 7 and Ubuntu 16.4 in dual boot two hdd's"
date: 2016-08-17
forum: New to Ubuntu
---

### Post by longshanks62 on 2016-08-17
Hello.
I am newish to ubuntu having tried booting ubuntu 12 from a usb stick into my windows 7 pc and playing with it. I now want to install 16.4 as a second O/S on a 2nd installed HDD on my PC and then run it as a dual boot system. What I need is an easy step by step guide. 
regards

---

### Post by yancek on 2016-08-17
The link below has a very detailed guide on 14.04 including a step by step guide on dual booting.  You would need to be familiar with Linux device/partition naming conventions which is explained at the link.  Use the manual "Something Else" option as it will give you more control, especially since you want to install to a second disk.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by grahammechanical on 2016-08-17
This is how I would do it.

1) Disconnect the Windows drive
2) Install Ubuntu on the only drive left in the machine using the Erase disk and install Ubuntu option.
3) Restart and test that Ubuntu loads and then shut down.
4) Reconnect the Windows drive.
5) Restart and load Ubuntu. There will be no boot menu and no option to load Windows.
6) Open a terminal and run this command

[code]sudo update-grub[/code}

Watch the printout. It should include a listing for a Windows boot loader.

7) Shutdown Ubuntu and restart. There should now be a boot menu with options to load either Ubuntu or Windows.
8) Test the boot menu.

If you set the BIOS to look for an OS on the Ubuntu drive you will get a boot menu (Grub) with options to load either Ubuntu or Windows. If you set the BIOS to look for an OS on the Windows drive then Windows will load. There will be no option to load Ubuntu.

The Ubuntu installer defaults to installing the Ubuntu boot loader (Grub) into the MBR of the first hard drive (sda). If that is the Windows drive it will over-write the Windows boot loader. With two hard drives and Ubuntu on the second drive (sdb) we have to specifically instruct the Ubuntu installer to install Grub into the MBR of the second hard drive (sdb). 

With only one drive in the machine we avoid that little complication.

Regards

---

