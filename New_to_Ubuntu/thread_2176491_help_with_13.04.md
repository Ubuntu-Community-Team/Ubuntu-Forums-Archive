---
title: "help with 13.04"
date: 2013-09-24
forum: New to Ubuntu
---

### Post by giz@ on 2013-09-24
I've got a few issues with 13.04 on my acer aspire 5742z.
Firstly firefox hangs at start up, after a few minutes the home page appears but then freezes after any link is clicked or web address input. Chromium works beautifully. 
Secondly usb fails to mount i get the following error 
  ```
Error checking authorization: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.udisks2.filesystem-mount is not registered (polkit-error-quark, 0)
```
Thirdly downloads folder opens and then closes before being able to access any documents.
Lastly i've got dummy output in sound settings but none of the suggestions i've found from previous topics have worked as i get errors in terminal.

Any help will be greatly appreciated.

Paul

---

### Post by giz@ on 2013-09-24
i just remembered one more thing, i can't shut down or reboot unless i use terminal, if i choose shutdown it just logs me out.

---

### Post by ajgreeny on 2013-09-24
Distro upgrade to 13.04 or new, clean installation?

Did a previous version all work as expected?  If so I wonder if your DVD/USB or the .iso file it was produced from is a good one.  Check the .iso file md5sum, and if that's OK try making another DVD or USB.

Can you login as guest (or another user) to see if the troubles persist.

---

### Post by giz@ on 2013-09-25
Fresh install, md5sum matched. unfortunately i've deleted the iso so i'll have to download it again to make a new disc.
I'm getting system error report problem messages today.

The last distro i had was mint 11, i had 2 problems with that - the touchpad would lockup after hibernation and occasionally the menu was invisible.

Login as guest session makes no difference...

---

### Post by dshgna on 2013-09-25
> **giz@ said:**
> i just remembered one more thing, i can't shut down or reboot unless i use terminal, if i choose shutdown it just logs me out.

I have this same issue. Choosing shut down after being logged out works, but ts an additional step which I'd prefer to do without as I am the only user.

---

### Post by giz@ on 2013-09-25
choosing shutdown at the next screen doesn't work, the tab changes colour but nothing happens.

---

### Post by giz@ on 2013-09-26
the one thing i should add is that all of these things worked when i first installed 13.04 about a month ago. could it be an update that has cocked it all up? is there a way of turning back the clock?

---

### Post by varunendra on 2013-09-27
> **giz@ said:**
> the one thing i should add is that all of these things worked when i first installed 13.04 about a month ago. could it be an update that has cocked it all up? is there a way of turning back the clock?

Unless manually removed, older kernels are retained during upgrades. So you should be able to boot with an older kernel and see if it works fine again.

If you don't see the advance Grub menu by default (from where you can choose to boot with older kernel), press "Shift" key (or "Esc" in some systems) during the purple splash screen. In the menu screen that comes up, you should get the option to boot with older kernels in the third line from top.

To see which kernels you have installed, you may use the following command -
```
dpkg -l | grep linux-image
```

To see which one you are currently running -
```
uname -r
```

By the way, the problems you have described in the first post seem to be a result of a broken update or some corrupt package(s), not kernel bugs.

---

### Post by giz@ on 2013-09-28
> **varunendra said:**
> Unless manually removed, older kernels are retained during upgrades. So you should be able to boot with an older kernel and see if it works fine again.

If you don't see the advance Grub menu by default (from where you can choose to boot with older kernel), press "Shift" key (or "Esc" in some systems) during the purple splash screen. In the menu screen that comes up, you should get the option to boot with older kernels in the third line from top.

To see which kernels you have installed, you may use the following command -
```
dpkg -l | grep linux-image
```

To see which one you are currently running -
```
uname -r
```

By the way, the problems you have described in the first post seem to be a result of a broken update or some corrupt package(s), not kernel bugs.

Is there away of repairing the update or undoing it?

---

### Post by varunendra on 2013-09-28
> **giz@ said:**
> Is there away of repairing the update or undoing it?

There is no easy way to fully roll back, but if you can boot with an older kernel, you can try this *(be careful, read the messages before proceeding, if something prompts to remove too many things at once, stop, and post back that message)* -
```
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade
```
Reboot normally and see if it works any better.

To do something close to an 'Undo', you can choose to remove the newer kernel(s) before performing above. The last command will most probably install/reinstall the latest recommended kernel, along with other packages.

---

### Post by giz@ on 2013-09-30
tried the above in terminal, it's made no difference. :(
i've also tried using all kernals listed and they all have the same faults. live cd works fine.

---

### Post by varunendra on 2013-09-30
> **giz@ said:**
> tried the above in terminal, it's made no difference. :(

While being in the older kernel or the current one? By default, you'll obviously boot into the current one. You have to try those commands while you have booted with an older, working kernel (which you can only choose from the grub menu).

And if you did boot with the older kernel, was everything working fine there? Like before?

---

### Post by giz@ on 2013-09-30
i hit shift at start up and chose the oldest kernel from grub, all faults remain.

---

### Post by giz@ on 2013-09-30
it can see the audio controller......

lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
02:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

---

### Post by giz@ on 2013-09-30
i've just tried to open software and updates and nothing happened.

so i tried 
 software-properties-gtk --open-tab=4


Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 103, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 93, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 105, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 593, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python3/dist-packages/aptsources/distro.py", line 87, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template
[1]+  Exit 127                software-

still not opening.

---

### Post by giz@ on 2013-09-30
gksudo gedit /etc/lsb-release  


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"

---

