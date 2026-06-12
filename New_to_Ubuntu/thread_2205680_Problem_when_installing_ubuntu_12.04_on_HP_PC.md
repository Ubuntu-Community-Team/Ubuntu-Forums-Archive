---
title: "Problem when installing ubuntu 12.04 on HP PC"
date: 2014-02-15
forum: New to Ubuntu
---

### Post by ruben6 on 2014-02-15
Hello everybody,

Today after fully reading all the indications of getgnulinux.org about how to install linux I decided to try it myself. I downloaded the iso of ubuntu 12.04 and burned it on my 4GB usb with a program called ISOtoUSB. I booted from the usb, and installed linux, but after being asked to reestart to finish the installation, it was not possible to select any linux, as if it hadn't been installed. 

Furthermore, when I opened windows, there was some sort of problem with the temp folder and the hard drive seemed to be damaged after installing linux (maybe because of the partition that linux automatically does?). I really dont know what went wrong.

I (think) managed to fix the hard drive problems, but still there is no option to start with linux. Any ideas on how to fix it?

Thanks a lot!

---

### Post by oldfred on 2014-02-15
Best to see details. You can install this into your live installer flash drive.

 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by cogier2 on 2014-02-15
Have a look at this [boot repair software ]("http://sourceforge.net/projects/boot-repair-cd/files/")

---

