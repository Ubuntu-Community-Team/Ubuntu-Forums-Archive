---
title: "uninstalling displaylink driver"
date: 2021-10-29
forum: New to Ubuntu
---

### Post by nginmu on 2021-10-29
Followed the instructions here:

[https://support.displaylink.com/knowledgebase/articles/684649](https://support.displaylink.com/knowledgebase/articles/684649)

Everything went ok & the hardware started working.

Changing to a different style of hardware now & need to uninstall the above driver.

Unfortunately, where they say ''8. For uninstallation procedure see here.", the link seems to be missing.

I had a brief look in Muon and Synaptic to see if I could uninstall it from there somehow but nothing obvious to a relative newcomer to linux like me.

Any suggestions gratefully received.

EDIT

ahh.. think I might have found it.. [https://support.displaylink.com/knowledgebase/articles/683699-how-to-uninstall-displaylink-ubuntu-software](https://support.displaylink.com/knowledgebase/articles/683699-how-to-uninstall-displaylink-ubuntu-software)

Below is the response I got in terminal. Everything seems to have gone as it should?

```

me@me-pc:~$ sudo displaylink-installer uninstall
[sudo] password for me: 
DisplayLink Linux Software 5.4.1-55.174 install script called: uninstall
Distribution discovered: Ubuntu 21.04

Uninstalling

[ Removing EVDI from kernel tree, DKMS, and removing sources. ]
dkms remove evdi/1.9.1 --all

-------- Uninstall Beginning --------
Module:  evdi
Version: 1.9.1
Kernel:  5.11.0-34-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

evdi.ko:
 - Uninstallation
   - Deleting from: /lib/modules/5.11.0-34-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.....

DKMS: uninstall completed.

-------- Uninstall Beginning --------
Module:  evdi
Version: 1.9.1
Kernel:  5.11.0-39-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

evdi.ko:
 - Uninstallation
   - Deleting from: /lib/modules/5.11.0-39-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.....

DKMS: uninstall completed.

------------------------------
Deleting module version: 1.9.1
completely from the DKMS tree.
------------------------------
Done.
rm -f -rf /usr/src/evdi-1.9.1
Stopping displaylink-driver systemd service
[ Removing suspend-resume hooks ]
[ Removing udev rule ]
[ Removing Core folder ]

Uninstallation steps complete.
Please note that the evdi kernel module is still in the memory.
A reboot is required to fully complete the uninstallation process.
me@me-pc:~$ 


```

---

### Post by ActionParsnip on 2021-10-29
Run
```

lsmod | grep evdi

```

If you see it listed then this is what the script is talking about. You can remove it with
```

sudo modprobe -r evdi

```

---

### Post by nginmu on 2021-10-29
Thanks.

Seems I never needed the latest displaylink-driver-5.4.1-55.174.run (or even displaylink-driver-5.4.0-55.153.run, the specific driver Startech recommend for their USB32DVIPRO DVI / DL-3100 device) when I was using the older VGA / DL-165 device.

Turns out my old Lindy 42744 VGA / DisplayLink DL-165 based device, didn't use the newer DisplayLink driver but was running using the "Open source UDL driver".

Must just have been coincidence my old device started working at the point when I tried loading the new driver.

Uninstalling displaylink-driver-5.4.1-55.174.run and then reloading displaylink-driver-5.4.0-55.153.run seems to have allowed the new Startech device to start working. Or again maybe coincidence.

Maybe I'll try removing displaylink-driver-5.4.0-55.153.run now, reloading displaylink-driver-5.4.1-55.174.run, (it's newer?)  and see if it keeps working :-)

The newer DL - 3100 / 512Mb / DVI device despite not having USB3 available, is working on USB2 much much better than the old DL-165 / 8Mb / VGA device, difference between usable and not.

Will mark as solved & go look up about modprobe :-)

---

