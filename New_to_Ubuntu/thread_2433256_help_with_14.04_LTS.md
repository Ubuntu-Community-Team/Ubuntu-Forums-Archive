---
title: "help with 14.04 LTS"
date: 2019-12-16
forum: New to Ubuntu
---

### Post by fox-linux on 2019-12-16
i have a big problem
i am using an ubuntu 14.04 LTS in a HP 15 notebook pc
the problem is mounting 
i can`t mount an usb, hard disk or even a cd
it says this:
Error checking authorization: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.udisks2.filesystem-mount is not registered (polkit-error-quark, 0)
i have tried many options but none of them workedt t using 
earlier it was working until i tried to install TURBO C++ using wine
I think it changed some settings  
I tried to mount it using terminal but it says that the file is not found in /etc/fstab or /etc/mtab.
this laptop had 2 OS a windows and the linux
Windows does not work because one day while the OS was updating my computer shut off
then it started giving me error messages
the ubuntu runs in a 50 GB partition and i cannot mount other partitions in the same hard disk.
PLEASE HELP!!

---

### Post by Impavidus on 2019-12-16
It sounds like you've got a problem with mounting things using the GUI and are not so familiar with mounting using the command line.

Ubuntu 14.04 is no longer supported. That means, no more updates and we don't support it either. We can help you to copy files to backup storage and install a supported release of Ubuntu (I suggest 18.04).

---

### Post by yancek on 2019-12-16
In addition to updating to a current release, when posting in the future post relevant information.  You indicate you tried to mount but neglect to indicate "how" you did that.  If you were using some GUI method or if you used a terminal command you should post exactly what it was.    The message about not being found in fstab or mtab is generally because you did not  do a complete mount command, referring specifically to the device partition.  It is always a good idea to keep notes when you are installing new software such as you were so that if you run into problems, you have some information on what you did which you can post and hopefully, someone will be familiar with the software and can help.

---

