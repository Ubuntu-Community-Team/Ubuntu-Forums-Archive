---
title: "virtual machine obtaining wrong IP"
date: 2012-05-27
forum: New to Ubuntu
---

### Post by hookitup on 2012-05-27
so i have a virtual machine running Mint and the physical pc is ubuntu 12.04, i am not getting an 192.168.1.X address on the virtual machine, im getting like a 10.0.2.x address, im pretty sure it has something to do with the virtual nic or however that works, how can i obtain a 192.168.1.x address on the virtual machine ?


Thanks for the help

---

### Post by mlentink on 2012-05-28
Sorry, your question is not answerable without some essential information. What virtualization software did you use to set up the VM?

---

### Post by Cheesemill on 2012-05-28
You need to change the network adapter on the VM to Bridged mode, it sounds like it is in NAT mode which is the default for VM's

---

### Post by Dave_in_MD on 2012-05-28
> **hookitup said:**
> so i have a virtual machine running Mint and the physical pc is ubuntu 12.04, i am not getting an 192.168.1.X address on the virtual machine, im getting like a 10.0.2.x address, im pretty sure it has something to do with the virtual nic or however that works, how can i obtain a 192.168.1.x address on the virtual machine ?


Thanks for the help

Sounds like virtualBox.  If so this is normal,  the VB software acts as a NAT/DHCP, between the host OS, which will get the network address either statically assigned by you or more commonly by DHCP and the guest OS. The virtual systems I use at work always have a 10.0.x.x where the copper network I am connecting to is 172.16.x.x or 172.17.x.x depending on which domain, admin or student, I am working with.  It still works fine if I export the VM put it on a 65.x.x.x external, or bring it home for an experiment  on my 192.168.x.x home network.

---

### Post by haqking on 2012-05-28
its a NAT address in this example, change it to bridged mode and get on that way or assign it a static in bridged mode,.

Either way change the VM NIC settings.

Peace

---

### Post by hookitup on 2012-05-28
Thanks for the help, i have successfully switched it from NAT to bridge.

---

### Post by haqking on 2012-05-29
> **hookitup said:**
> Thanks for the help, i have successfully switched it from NAT to bridge.

Cool, remember to mark the thread as solved using thread tools menu.

Cheers

---

