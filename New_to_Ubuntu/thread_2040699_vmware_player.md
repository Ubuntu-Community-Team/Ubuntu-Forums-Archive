---
title: "vmware player"
date: 2012-08-11
forum: New to Ubuntu
---

### Post by edsh on 2012-08-11
Is posibile to install vmware player@ ubuntu in a pc that do not support Virtualization technology!?!?!???!?!?
Regards Edsh

---

### Post by Ms. Daisy on 2012-08-11
What? Why doesn't your pc support virtualization?

vmware player is just an app that you install on (presumably) Ubuntu that allows you to virtualize other operating systems.  Have you read about [VMWare Player]("http://www.vmware.com/products/player/") at all?

---

### Post by edsh on 2012-08-11
I dont know why...when i try look for it after i hav an application on windows xp for verify if my pc support virtualization technology i gave a message like this : This computer does not have hardware-assisted virtualization.... 
Sorry I dont understand waht u say its possibile toio install it without VT
Regards edsh

---

### Post by Ms. Daisy on 2012-08-11
Can you take a screen shot of the error and post it here?

I *think* the message is telling you that you can't use graphics card acceleration in vmware.  But you should still be able to use vmware to create a virtual machine.

---

### Post by ads52 on 2012-08-11
Hardware assisted virtualisation simply means that the host cpu explicitly supports guest machine machines and this considerably reduces performance overhead for both host *and* guest. Software virtualisation is still possible and should work well enough.

Just be aware that sometimes the hardware virtualisation option can be turned on and off in the bios, with all of the attendant risks of mucking around in this vital area of your computer :).

---

