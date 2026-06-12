---
title: "overheating + related concerns"
date: 2020-08-03
forum: New to Ubuntu
---

### Post by lelmst on 2020-08-03
New ubuntu user here
I have switched to the default gnome 3 ubuntu after pop!_OS sent my cpu up to 96°C while installing packages and other high temperatures, and budgie failed to get my nvidia card to work.
The nvidia card works now, but I know that they tend to be problematic and that may be involved.
Now my issues are a battery life of 3 hours rather than 8 on windows, higher than usual cpu temperature, and the computer always failing to boot during restarts. I have to stare at the Asus logo for 20 minutes if I try to restart and force a shutdown, but powering on and waking from sleep work fine.
BIOS and other firmware was updated a week ago under windows, just a couple days before testing linux, and nearly everything other than the things I've mentioned work well right now.
A friend thinks it's probably an issue with firmware communicating with the kernel.

---

### Post by CelticWarrior on 2020-08-03
Installing Nvidia drivers is as simple as disabling Secure Boot in UEFI (what you call "BIOS" but really isn't), boot Ubuntu (with additional boot parameter 'nomodeset' if the graphical interface doesn't start and/or it freezes), open Additional Drivers, select and apply the recommended Nvidia proprietary drivers. Exceptions are some very specific cards that need very specific drivers versions or a brand new Nvidia card for which our current release hasn't the proper drivers yet in the repository in which case we add an additional software source, the graphics drivers PPA and then install the newer driver version required. Installing the proprietary drivers usually also takes care of the overheating problem.

The second issue here is a comparison that is being made out of ignoring the hybrid graphics and how Windows and most Linux distros deal with those:
- In Windows you're almost always working with the energy efficient integrated graphics and not with the discrete Nvidia graphics. The latter only works when switch on to it by a software that requests high performance. This switch is not always perceivable to the user.
- OTOH, in most Linux distros the switch has to be done manually and set after a reboot. Typically in the Linux desktop the high performance profile (Nvidia) is the default and users need to change it to the energy saving profile (Intel or other integrated graphics). Thios can be done at the Nvidia X Server Settings app > Profiles. Once done and after a reboot you'll be working with the integrated graphics and so, provided the relative workload is the same as in Windows, you should obtain roughly the same battery performance.

Please post your complete hardware specifications if you need further help with specifics.

---

### Post by lelmst on 2020-08-03
The EFI partition has been wiped and replaced and the BIOS has been flashed before installing. I also disabled secure boot and still have it disabled.
So when I installed ubuntu I chose the option to install the recommended proprietary software including graphical drivers. Does that cover the correct driver already or are there exceptions? I have the GeForce GTX 1050 2GB card. Updating the driver directly from the website failed after 2 hours in Pop!_OS, where the card never loaded, but it loads now so I haven't bothered with reinstalling it.
How do I add the nomodeset parameter?
Oh yes I do remember messing with the nvidia x server settings app in the latter 2 flavors. The integrated graphics only setting caused some serious overheating each time, and the setting that makes use of the nvidia card at all times produced the least amount of lag and heat output, at the expense of draining battery much more quickly. I mostly have been testing the switching option, though it hasn't solved either problems but it does produce the best results. I do know that the card is working but I'm not sure if it's working as well as it could.
Here is the laptop model with its specs:
[https://www.asus.com/us/Laptops/Q536FD/specifications/](https://www.asus.com/us/Laptops/Q536FD/specifications/)

---

### Post by CelticWarrior on 2020-08-03
So much confusion...

YES, in the latest release - 20.04 - if you selected the option to install graphical drivers it will do that (hopefully the correct version is installed) and with Secure Boot disabled the drivers will work properly. NO ADDITIONAL PARAMETER REQUIRED. 'nomodeset' is use ONLY in the aforementioned situations. Even if you need to install the proprietary drivers you DON'T use 'nomodeset' if the open-source driver is enough to have a working desktop. 

> [COLOR=#000000]The integrated graphics only setting caused some serious overheating each time, and the setting that makes use of the nvidia card at all times produced the least amount of lag and heat output, at the expense of draining battery much more quickly.[/COLOR]

That means that very likely you're "abusing" the Intel Graphics for tasks where the dGPU is more suited to deal with. Intel Graphics work perfectly fine and INDISTINGUISHABLE from Windows as long as the workload is comparable. 

So, at the end of the day, you actually know how it works and what to expect. Keep in mind that Windows does the switch seamlessly, Linux doesn't. If you - the user - isn't changing it manually then you CAN'T compare apples with oranges and making this kind of posts is a waste of time, both for you and other user here.

Have a nice day.

---

### Post by lelmst on 2020-08-03
I figured out that if I open BIOS setup I can consistently get it to boot after a restart so that solves the 'unable to restart' issue
One final concern: is there anything I can do to reduce the high power consumption and excessive heat?

---

### Post by Impavidus on 2020-08-03
> **lelmst said:**
> ... the least amount of lag and heat output, at the expense of draining battery much more quickly. 

That's remarkable, as all the energy that goes out of the battery is converted into heat.

---

### Post by lelmst on 2020-08-03
the heat is more distributed i mean, with more of it being at the gpu, rather than all of it being concentrated at the cpu's location making it far hotter than when the gpu is also in use.
with the nvidia card being on at all times, despite that more energy is being used and more total heat is being generated, it's coming from the gpu as well and less is coming from the intel chip.
so i am far less concerned with overheating. should have been more clear

---

### Post by QIII on 2020-08-03
I think Impavidus was indicating that heat and power are intertwined.  You are not going to get "all the power without the heat".

---

### Post by daniewicz on 2020-08-03
Have you tried installing and running powertop to increase battery life?

---

### Post by lelmst on 2020-08-03
What do I do about this
>> Bad           Enable SATA link power management for host0                                                            
   Bad           Enable SATA link power management for host1
   Bad           Enable SATA link power management for host2
   Bad           VM writeback timeout
   Bad           Autosuspend for USB device Touchscreen [ELAN]
   Bad           Runtime PM for port ata1 of PCI device: Intel Corporation Cannon Point-LP SATA Controller [AHCI Mode]
   Bad           Runtime PM for port ata2 of PCI device: Intel Corporation Cannon Point-LP SATA Controller [AHCI Mode]
   Bad           Runtime PM for port ata3 of PCI device: Intel Corporation Cannon Point-LP SATA Controller [AHCI Mode]
   Bad           Runtime PM for disk sda
   Bad           Runtime PM for disk sdb

---

### Post by mastablasta on 2020-08-04
> **lelmst said:**
> Updating the driver directly from the website failed after 2 hours in Pop!_OS, where the card never loaded, but it loads now so I haven't bothered with reinstalling it.


you should install it from repositories, not directly from website. for beta drivers you would use the PPA.
for example:
[https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-20-04-focal-fossa-linux)

---

### Post by daniewicz on 2020-08-04
[HTML]What do I do about this
>> Bad Enable SATA link power management for host0
Bad Enable SATA link power management for host1
Bad Enable SATA link power management for host2
Bad VM writeback timeout
Bad Autosuspend for USB device Touchscreen [ELAN]
Bad Runtime PM for port ata1 of PCI device: Intel Corporation Cannon Point-LP SATA Controller [AHCI Mode]
Bad Runtime PM for port ata2 of PCI device: Intel Corporation Cannon Point-LP SATA Controller [AHCI Mode]
Bad Runtime PM for port ata3 of PCI device: Intel Corporation Cannon Point-LP SATA Controller [AHCI Mode]
Bad Runtime PM for disk sda
Bad Runtime PM for disk sdb[/HTML]

select each one individually and then press enter to toggle

---

