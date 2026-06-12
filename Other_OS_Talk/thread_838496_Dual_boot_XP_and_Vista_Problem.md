---
title: "Dual boot XP and Vista Problem"
date: 2008-06-23
forum: Other OS Talk
---

### Post by SIXAXIS on 2008-06-23
Hi guys,

Here is the story, I had Windows Vista installed and then I partitioned the HDD. I installed XP and used the Vista DVD to allow me to boot up in Vista. I installed VistaBootPRO and added Windows XP to my bootloader. When I try to go into XP, it gives me an error and the only thing I can do is restart or go back to the bootloader to choose Vista.

**EDIT:** The error is saying that the file cannot be found. I checked VistaBootPRO and found out that it did not set the bootloader right. Is there a way I can just uninstall the Vista bootloader and use GRUB? The file was NTLDR, and it is looking for it in D:/ntldr. I don't know if that is the correct spot for it and I don't know if the drive letter is right because from Vista, hte XP partition is D, and from XP, the XP partition is E.

---

### Post by SIXAXIS on 2008-06-23
This is what VistaBootPRO is telling me for the BCD Registry:
```
Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  unknown
default                 {current}
displayorder            {current}
                        {ntldr}
timeout                 20

Windows Boot Loader
-------------------
identifier              {6c93c258-1ed8-11dd-adb6-fc8cb0ce8a02}
device                  unknown
path                    \Windows\system32\winload.exe
description             Windows Vista (TM) Home Premium (recovered) 
osdevice                unknown
systemroot              \Windows
resumeobject            {f24c9e93-1eb8-11dd-99ad-806e6f6e6963}

Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Windows Vista (TM) Home Premium
osdevice                partition=C:
systemroot              \Windows
resumeobject            {6f85d722-2558-11dd-9ef9-806e6f6e6963}

Resume from Hibernate
---------------------
identifier              {6f85d722-2558-11dd-9ef9-806e6f6e6963}
device                  partition=C:
path                    \Windows\system32\winresume.exe
description             Windows Vista (TM) Home Premium (recovered) 
inherit                 {resumeloadersettings}
filedevice              partition=C:
filepath                \hiberfil.sys
debugoptionenabled      No

Resume from Hibernate
---------------------
identifier              {f24c9e93-1eb8-11dd-99ad-806e6f6e6963}
device                  unknown
path                    \Windows\system32\winresume.exe
description             Windows Vista (TM) Home Premium (recovered) 
inherit                 {resumeloadersettings}
filedevice              unknown
filepath                \hiberfil.sys
debugoptionenabled      No

Windows Memory Tester
---------------------
identifier              {memdiag}
device                  unknown
path                    \boot\memtest.exe
description             Windows Memory Diagnostic

Windows Legacy OS Loader
------------------------
identifier              {ntldr}
device                  partition=D:
path                    \ntldr
description             Windows XP

```

**EDIT:** Oh yeah, I should've said that this data cannot be edited by typing in it. You have to select the options and stuff and VistaBootPRO does it for you. Wow, I can't believe this is causing this much trouble. I hate Windows.

---

### Post by SIXAXIS on 2008-06-23
Do you think that I should install Ubuntu on a smaller 2GB partition and then use that as a location for the GRUB bootloader? I can then customize it to only say Vista and XP.

---

