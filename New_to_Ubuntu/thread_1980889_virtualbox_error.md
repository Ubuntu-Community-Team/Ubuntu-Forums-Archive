---
title: "virtualbox error"
date: 2012-05-16
forum: New to Ubuntu
---

### Post by idom on 2012-05-16
Hi I am running 10.04 LTS and was using virtual box XP without any problem suddenly it is giving following error.


Failed to open a session for the virtual machine xp1.
VT-x features locked or unavailable in MSR. (VERR_VMX_MSR_LOCKED_OR_DISABLED).

Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {1968b7d3-e3bf-4ceb-99e0-cb7c913317bb}

please help

---

### Post by QIII on 2012-05-16
In the settings of the virtual machine, do you have "Enable VT-x/AMD-V" checked under System --> Acceleration?

Is your BIOS set to allow virtualization?

---

### Post by idom on 2012-05-16
> **QIII said:**
> In the settings of the virtual machine, do you have "Enable VT-x/AMD-V" checked under System --> Acceleration?

Is your BIOS set to allow virtualization?

Thanks once I removed it started working. Still facing some problem with mouse setting . I am not sure what is the problem is and it keeps refusing to boot without safe mode.

as I don't have much data in windows I am thinking reinstalling might be a better option.

idom

---

