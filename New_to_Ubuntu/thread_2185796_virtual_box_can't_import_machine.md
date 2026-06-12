---
title: "virtual box can't import machine"
date: 2013-11-04
forum: New to Ubuntu
---

### Post by amgdega on 2013-11-04
I exported a virtual box machine (WinXP guest on Ubuntu 12.04 host) and tried to import it in another Ubuntu 12.04 pc. The file .OVF was not imported by Vbox in the second pc (where another WinXP guest machine is perfectly working) because of this error:

Failed to import appliance /home/ginus/VirtualBox VMs/gingHP.ovf.

Could not create the directory '/h...s/VirtualBoxVMs/ginguswinn_1' (VERR_ACCESS_DENIED).

Result Code: VBOX_E_IPRT_ERROR (0x80BB0005)
Component: Appliance
Interface: IAppliance {3059cf9e-25c7-4f0b-9fa5-3c42e441670b}

I already tried many different solutions from forums (both Ubuntu and Vbox ones)
No way to import that machine.
Any hint?

---

### Post by daanskitte on 2013-11-04
Try cloning the machine instead.

Open VirtualBox and right-click on your WinXP machine -> Clone...
Once the cloning is complete, right-click on the WinXP _Clone_ and select 'Show in file manager'
Copy the whole cloned folder onto your new machine. Unless you renamed the clone it should be called something like 'WinXP Clone'
Open VirtualBox on your other computer and select Machine -> Add... from the taskbar. Browse to the 'WinXP Clone' folder and add the cloned hard drive.

That should do the trick!

---

### Post by NM5TF on 2013-11-04
check the permissions of the .ovf file......I had the same  problem until
I changed the permissions to all users read/write

Tommy

---

### Post by amgdega on 2013-11-13
Thanks [COLOR=#000000]daanskitte & NM5TF, [/COLOR]I tried both your suggestions but no way: I get always the same error message....
Thank you anyway

---

