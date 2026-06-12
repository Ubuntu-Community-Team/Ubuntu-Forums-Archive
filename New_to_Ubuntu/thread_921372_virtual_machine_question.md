---
title: "virtual machine question"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by boblemur on 2008-09-16
i know this is going to sound rather odd, because it basically defeats the purpose of a virtual machine completely but...


am i able to give a virtual machine direct access to a certain pci device (sound card in this case) so that i can use another operating system's drivers to play my music.


i know it sounds like a lot of work and a rather stupid idea, but my music is extremely important to me, but my sound card isnt supported in linux and i dont really have the money to buy another (i also dont have onboard sound)


thankyou for any help in advance

---

### Post by Mornedhel on 2008-09-16
As far as I know, virtual machines rely completely on the host OS to provide access to the hardware. No direct access is available. I might be wrong.

---

### Post by howefield on 2008-09-16
If it doesn't work in linux, I don't think you will get it to work in your vm.

What model sound card do you have ?

---

### Post by whizbaby on 2008-09-16
I read about VMs having loaded virtual graphics and sound cards devices (like eg nvidia gforce chipset) tailored so that the VM can use the real hardware device directly, but those features are only available for (much) money and not for all hardware.

---

### Post by boblemur on 2008-09-19
do you remember where you read about this?? or which virtual machine they were using?? because i find it hard to search when i dont know what product to try.

---

### Post by whizbaby on 2008-09-20
It was for VMware, but the features are not for free.
Im unable to find the site where I read that, it was at work an theres no browsing history...

---

### Post by boblemur on 2008-09-21
ok, thank you ill ask on the vmware forums :)

---

### Post by virtuallinux on 2008-09-21
I don't think it's possible to give a VM access to any physical device aside from a hard disk.  If it is possible, I've never heard of it. But then, the only virtualization software I have experience with is VMWare, so it may be possible in other software.

---

