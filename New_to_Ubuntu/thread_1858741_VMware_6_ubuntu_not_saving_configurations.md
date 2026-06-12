---
title: "VMware 6 ubuntu not saving configurations"
date: 2011-10-12
forum: New to Ubuntu
---

### Post by t-bo on 2011-10-12
Hi.  Long time lurker, first time poster.  

I am attempting to create a VMware ubuntu server on my Windows 7 laptop.  I have attempted this with Ubuntu 11.04 and 10.04.3 with identical results.

I do not have a CD available, so after creating my VM I go into VM-->Settings and point the VM's CD drive to my local windows disk where I have the Ubuntu .iso file stored.  

I can start the Ubuntu VM and configure it, but after I reboot the VM or restart it, all my configurations (such as users, ssh server, etc) are all gone.  Each time I reboot/restart the VM it's a fresh machine with no configs; like I was trying Ubuntu without installing it.  

I have tried interrupting the VM boot process and tell Ubuntu to "install Ubuntu".  It boots but I still get the same results - all configs are gone when I restart the VM.

I can't find this problem listed anywhere.

Any ideas?

Thank you,
Tim

---

### Post by sadaruwan12 on 2011-10-13
> **t-bo said:**
> Hi.  Long time lurker, first time poster.  

I am attempting to create a VMware ubuntu server on my Windows 7 laptop.  I have attempted this with Ubuntu 11.04 and 10.04.3 with identical results.

I do not have a CD available, so after creating my VM I go into VM-->Settings and point the VM's CD drive to my local windows disk where I have the Ubuntu .iso file stored.  

I can start the Ubuntu VM and configure it, but after I reboot the VM or restart it, all my configurations (such as users, ssh server, etc) are all gone.  Each time I reboot/restart the VM it's a fresh machine with no configs; like I was trying Ubuntu without installing it.  

I have tried interrupting the VM boot process and tell Ubuntu to "install Ubuntu".  It boots but I still get the same results - all configs are gone when I restart the VM.

I can't find this problem listed anywhere.

Any ideas?

Thank you,
Tim

OK bro, You're trying to install the Ubuntu server on win 7 host using VMware.

What product are you using from vmware is it vmaware workstation or something else.

Any way I was using vmware for a long time in my ubuntu box but got frustrated and wanted to look for some thing full free.

And I found it Oracal VirtualBox (Former Sun VirtualBox) the only draw back it had was the unavailability of the usb function but after Oracal guys took over they gave that function as extension pack once that have been installed you could have a fully functioning virtual environment.

After the switch I was very happy and actually it didn't gave me any problem what so ever it's available for windows as well if you want to give it try goto [www.virtualbox.org]("http://www.virtualbox.org").

And also it's pretty easy to learn mostly like the vmware one but it's much simpler.

Give it try I'm sure you'll going to love it.

---

### Post by t-bo on 2011-10-13
Hi sadaruwan12.  I'm using VM Workstation 6.  

So I actually have a solution for this but am not sure exactly why it worked; I can think of a few reasons why it may have though.  I uninstalled Workstation 6 and installed the most recent VM Player and it worked completely fine.  I followed the same setup steps with Player as I did with Workstation.  

I'm wondering if there's a compatibility problem with Workstation 6 (an older version) and the 10.04 and 11.04 Ubuntu loads.  Or, maybe it was a problem with 64 bit compatibility (Player is explicitly 32 or 64 bit capable).  

I may try virtual box though at some point.

Thanks!

---

### Post by sadaruwan12 on 2011-10-13
VMware 6 is very old and you could have been suffering from permission issues to access files and to write them on to the virtual hard disk.

Any way you should try Virual Box 'cos I know I was a die hard fan of vmware workstation 7.1 on Linux and theres no issue with the virtual PC if the host computer has enough resources to share with it's gust system.

And please mark the thread as solved as you managed to solve the problem.

THX

---

