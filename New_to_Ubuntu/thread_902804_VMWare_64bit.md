---
title: "VMWare 64bit"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by shodan on 2008-08-27
2 Days ago i installed VMware 1.0.6 build-91891 on 64bit ubuntu.
I installed 64bit XP on it and it was working fine for a day.

Today i try to run it and i get this error:
> 
This CPU is VT-capable, but VT is not enabled (check your BIOS settings).
You have configured this virtual machine as a 64-bit guest operating system.  However, this host's CPU is not capable of running 64-bit virtual machines or this virtual machine has 64-bit support disabled.
For more detailed information, see [http://www.vmware.com/info?id=152](http://www.vmware.com/info?id=152)


Any idea what happened? Only major thing i did was clone whole ubuntu partition... maybe thats why?

---

### Post by cliffa3 on 2008-09-14
Same thing just happened to me.  Had it up and running fine last night, only thing I did was a windows update and ubuntu update.  Vista 64-bit here.

---

### Post by drs305 on 2008-09-14
FWIW, virtualbox 2.0 runs fine on 64-bit. You just have to enable the VT option.

---

### Post by cliffa3 on 2008-09-14
I paid for vmware workstation and it does work fine.  This issue would have been the same with anything else, because for some reason the VT was disabled on bootup.  Nothing but a cold boot will solve it, so even going into the BIOS and making sure it's set doesn't help because that's a warm boot.  Completely power off and power back on and it should work if it has worked before.  Read somewhere on an intel page that the VT enabled/disabled won't change unless it's a cold boot, and I didn't change mine either...just got in a messed up state somehow.  Hopefully that's your problem too, good luck.

---

