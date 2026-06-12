---
title: "VM's - 1 as a server?"
date: 2012-02-25
forum: New to Ubuntu
---

### Post by anewguy on 2012-02-25
Is it actually "doable" to put Ubuntu server edition in a virtual machine in my Ubuntu installation?  It doesn't have to be great, but my new machine is 8-core and I have 16GB of memory, so there should be plenty to set up a vm with more than enough resources.  This vm wouldn't be for media serving, etc. - just to mess with the server edition and perhaps try to back up my laptop and other PC's to the new machine.

Thanks in advance!

Dave ;)

---

### Post by sanderj on 2012-02-25
Yes, no problem.

The only you can't do - AFAIK - is running a VM in a VM.

---

### Post by Paqman on 2012-02-25
Go for it. There are probably more servers in the world running as virtualised instances than on bare metal these days.

---

### Post by Seq on 2012-02-25
> **anewguy said:**
> Is it actually "doable" to put Ubuntu server edition in a virtual machine in my Ubuntu installation?  It doesn't have to be great, but my new machine is 8-core and I have 16GB of memory, so there should be plenty to set up a vm with more than enough resources.  This vm wouldn't be for media serving, etc. - just to mess with the server edition and perhaps try to back up my laptop and other PC's to the new machine.

Thanks in advance!

Dave ;)

My home server is an old Athlon X2 with 4GB ram. The server itself is running Ubuntu Server, sharing a bunch of directories via NFS and Samba. The server also has KVM+libvirt, and hosts the following single-purpose Virtual Machines:

[LIST]
[*]Apt-cacher-ng - Caching apt packages. Somewhat useful if you have >1 machine running the same distro.
[*]Askozia - an asterisk-based appliance that runs my home phone.
[*]Mediatomb - A UPNP server that shares media over the network. I have it configured to do live transcoding for formats my PS3 doesn't understand. This server alone has 2048MB ram assigned to it.
[*]Legacy - This is an image of my old stand-alone server, with a few things I haven't split off to single-purpose VMs yet (openvpn, etc).
[/LIST]

I have not had any performance issues yet, and I'm doing media transcoding on years old hardware (Not sure of the exact age, but I got the CPU and motherboard very cheap, and more than four years ago). You should have no difficulty.

---

### Post by Seq on 2012-02-25
> **sanderj said:**
> Yes, no problem.

The only you can't do - AFAIK - is running a VM in a VM.

Depends on the hypervisor. KVM can be nested on AMD, though apparently there are still some issues on Intel. VMWare's ESXi 5 can host an additional ESXi 5 instance, but that nested instance can only run 32-bit VMs.

Unsure about Virtualbox or VMWare's desktop products.

---

### Post by anewguy on 2012-02-25
Jeez, do I feel stupid!  Virtualized servers - like I haven't heard of that a zillion times!  Thanks for waking me up on that one - it won't be a problem at all.

Thanks all!

Dave ;)

---

