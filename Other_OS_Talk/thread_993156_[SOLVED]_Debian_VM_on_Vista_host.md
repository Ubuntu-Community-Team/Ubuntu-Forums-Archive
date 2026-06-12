---
title: "[SOLVED] Debian VM on Vista host"
date: 2008-11-25
forum: Other OS Talk
---

### Post by DouglasAWh on 2008-11-25
I was using VMWare Player and things were working great, but a co-worker suggested VMWare Server since I don't want the Player rectangle in my taskbar all the time.  I can access the VMWare utility through [https://localhost:8333/ui/](https://localhost:8333/ui/), but I can't add VMs.  When I go to the link for adding VMs, I can't browse my computer, I can only see a datamart called "standard".  I'm fine moving my VM to "standard" but I don't know where that is.

Thanks!

---

### Post by kk0sse54 on 2008-11-26
I think you're approaching this the wrong way mate, you need to create a virtual hard drive which vmware will boot up just like a regular machine. Check out the links on this page [http://www.vmware.com/support/pubs/server_pubs.html](http://www.vmware.com/support/pubs/server_pubs.html) and especially read the Vmware user guide and Installing a Guest Operating System links

---

### Post by DouglasAWh on 2008-11-26
> **C!oud said:**
> I think you're approaching this the wrong way mate, you need to create a virtual hard drive which vmware will boot up just like a regular machine. Check out the links on this page [http://www.vmware.com/support/pubs/server_pubs.html](http://www.vmware.com/support/pubs/server_pubs.html) and especially read the Vmware user guide and Installing a Guest Operating System links

Created the virtual hard drive long ago...actually, I downloaded the VM from MindTouch.

So, VMWare server requires VMs to be in C:\Virtual Machines\ on Windows.  I'm familiar with Virtual Box mostly and I'm pretty sure you could navigate the entire system to pick VMs, but VMWare Server doesn't do that out of the box.

Anyway, I got it working.  Firefox requires a plugin for VMWare Server.  It's like a 12MB extension I think.  I couldn't get it working in Chrome, but I didn't try very hard.

---

