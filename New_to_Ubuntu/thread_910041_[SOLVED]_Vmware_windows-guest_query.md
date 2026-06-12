---
title: "[SOLVED] Vmware windows-guest query"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by donniezazen on 2008-09-04
Hello,

I am feeling great after installing Vmware Server now i can use Windows application in just a click instead of restarting. 

I am completely new to this virtual machine stuff. I want to know how to shutdown the virtual machine by just closing the window or by properly shutting down(start-->shutdown)as i used to do in a separate partition.
Am i going to lose my my data/setting after i restart the windows?

Thanks.

---

### Post by tybalt on 2008-09-04
Hello,
in order to avoid any conflict with your VM, you should always shut down properly the Guest VM, prior to hibernate or shutdown your host OS (i guess your host is Ubuntu now...). That is the best way to ensure you loose no data in your guest VM.

You do not loose any data when you restart your guest VM; everything is properly stored in VM files managed by VMWare; what is more: you can copy the VM files to a pendrive and literally move your VM, as is, to a new host machine with VMWare ACE (i did that recently, and took just 10 minutes!).
Moreover, you can create snapshots of your current guest VM status, prior to any major OS change, and roll-back to that point if something went wrong.

You can personalize the VMWare ACE "Power" toolbar in order to perform specific actions in your Guest VM; by default, these actions are mapped to: power-off, suspend, power-on and reset.

Hope this helps.

---

### Post by fiddledd on 2008-09-04
You might also want to give VirtualBox a try, it's in the repositories. It's what many people use who don't like VMware.

---

### Post by isomer on 2008-09-04
Hi

You need to treat the virtual machines you create as if they are "real" machines, e.g. shut down a Windows VM as if shutting down a physical PC running Windows.

As tybalt says, your virtual machine is stored in files on your host Ubuntu partition and is controlled via VMWare.  You can move the files around, back them up, copy them, etc - just be careful as you can easily cause VMWare to lose control of the VM by moving the files.

---

### Post by donniezazen on 2008-09-06
Thanks Guys. thanks a lot.

---

