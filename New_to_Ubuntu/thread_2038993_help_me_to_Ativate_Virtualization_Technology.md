---
title: "help me to :Ativate Virtualization Technology"
date: 2012-08-07
forum: New to Ubuntu
---

### Post by edsh on 2012-08-07
hi everyone!
I hav install ubuntu on vmware workstation.
I want to install a virtualization technology (VT) on ubuntu .
I take this command grep svm /proc/cpuinfo for Amd platform to look for if my hardware support VT, after i gave this command on terminal i take nothing, so I understand that my hw donot support VT.
Can any one help me to activate it from bios ?
I am waiting for your replays
 Best regards Edsh

---

### Post by Cheesemill on 2012-08-08
If your hardware doesn't support it you can't use it. It's as simple as that.

Just so I can double check what processor do you have?

---

### Post by 2F4U on 2012-08-08
Intel VT support is indicated by the vmx flag and not the svm flag. The svm flag is for AMD support with AMD-V enhancement.

---

### Post by coldraven on 2012-08-08
I have seen one old laptop that had an option in the BIOS to turn on virtualization.
But in my laptop it is just on all the time.

---

### Post by Cheesemill on 2012-08-08
> **coldraven said:**
> I have seen one old laptop that had an option in the BIOS to turn on virtualization.

This only has any effect if the CPU actually supports virtualization as well. From the OP's original post it looks as if his CPU doesn't support it at all.

@edsh

If you could post the full output of:
```
cat /proc/cpuinfo
```
then we can tell if if your CPU supports virtualization or not.

---

### Post by edsh on 2012-08-08
[@ Cheesemill]("http://ubuntuforums.org/member.php?u=559258")
Hi! here is the output of the command you gave me ...
I am waiting your answer...
Regards!

---

### Post by adam.d.clemons on 2012-08-08
Just to clarify the OP, you are trying to enable Virtualization on a VM so you can run Virtualization software inside of the VM? I've had very poor experience with this. 

You *can* run a VM inside of a VM, but the performance is such that it's unusable and impractical. If you are just trying to make sure you have VT enabled for your VM, and you're certain it's on in BIOS, then you can open the VM settings in VMWare and there is an option to force V/T for that VM, but that only improves the performance of the Virtual Guest on the Physical Host, running another guest on a virtual host *will not* have access to VT through the Virtual host.

Hope that made sense.

---

### Post by edsh on 2012-08-08
I do smth like this...(have a look at foto...) but nothing gone change :(

---

### Post by Cheesemill on 2012-08-08
Have you switched on Virtualization on your actual machine?

Boot into your physical machines BIOS and check.

---

### Post by edsh on 2012-08-08
I dont know how to switch on...please can you give some instructions..
thanks

---

### Post by adam.d.clemons on 2012-08-08
If you can check that box, then it is enabled, but you will not be able to use VT on VM's inside of your Ubuntu VM. If you want to run VMs on Ubuntu, install ubuntu on the physical machine. VMs inside of VMs don't work well. 

Ubuntu will not see VT from inside of VMWare.

---

### Post by Cheesemill on 2012-08-08
> **adam.d.clemons said:**
> If you can check that box, then it is enabled, but you will not be able to use VT on VM's inside of your Ubuntu VM. If you want to run VMs on Ubuntu, install ubuntu on the physical machine. VMs inside of VMs don't work well. 

Ubuntu will not see VT from inside of VMWare.

Not true.

The whole point of virtualizing the VT extensions is so that Ubuntu **will** see them.

I do agree that it is rarely something that you should do, the only time that I have used it was to test out ESXi by running it an a VM (I didn't have any spare hardware at the time). As ESXi refuses to install if it doesn't see the VT extensions the only way you can install it on a VM is by using the aforemetioned feature (this feature is only available on the beta for the next version of VMware Workstation).

---

### Post by Cheesemill on 2012-08-08
> **edsh said:**
> I dont know how to switch on...please can you give some instructions..
thanks
That depends on your motherboard.
What make and model is it?

---

### Post by edsh on 2012-08-08
soory I dont understaand what up?!

---

