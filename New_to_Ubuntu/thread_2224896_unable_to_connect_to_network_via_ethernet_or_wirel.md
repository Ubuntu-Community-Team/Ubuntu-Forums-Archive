---
title: "unable to connect to network via ethernet or wireless"
date: 2014-05-18
forum: New to Ubuntu
---

### Post by jahern on 2014-05-18
this is a new install of ubuntu 12.04 lts on a 32bit dell latitude 131L laptop that previously had xp.  it has a mobile amd sempron proc. 3500+.  all this from ubuntu details screen.  I attempted to install updates after loading the os from a usb drive and it failed to connect to the internet.  both cards are recognized under lspci:

network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev01)
ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

lsmod does not show e100

I've read some forums but am a noob and quite lost. 

thanks for any help.

---

### Post by jahern on 2014-05-18
also, the machine is hanging when I shut down.  it just shows the ubuntu logo for hours and I eventually kill it by pressing and holding the power button.  it will boot fine.  just not shut down.

---

### Post by wildmanne39 on 2014-05-18
Did you try to install additional driver? if so we will need to remove it first.
With:
```
sudo apt-get purge bcmwl-kernel-source
```
Then reboot and ehternet connection should work now, then do:
```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
```
Reboot

---

### Post by jahern on 2014-05-19
thanks for responding.  I tried [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get purge bcmwl-kernel-source
[/FONT][/COLOR]and got this:
[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]engineer@engineer:~$ sudo apt-get purge bcmwl-kernel-source


[sudo] password for engineer: 


Reading package lists... Done


Building dependency tree
       
Reading state information... Done


The following package was automatically installed and is no longer required:
  dkms


Use 'apt-get autoremove' to remove them.
\
The following packages will be REMOVED:
  bcmwl-kernel-source*


0 upgraded, 0 newly installed, 1 to remove and 64 not upgraded.


After this operation, 3,668 kB disk space will be freed.


Do you want to continue [Y/n]? y


(Reading database ... 145846 files and directories currently installed.)


Removing bcmwl-kernel-source ...


Removing all DKMS Modules


Done.


update-initramfs: deferring update (trigger activated)


Purging configuration files for bcmwl-kernel-source ...


update-initramfs: deferring update (trigger activated)


Processing triggers for initramfs-tools ...


update-initramfs: Generating /boot/initrd.img-3.11.0-15-generic




and that's where it stops.

---

### Post by jahern on 2014-05-19
I shut the terminal down even though it said it was not done and then rebooted.  I tried the same command again and got this:

```
engineer@engineer:~$ sudo apt-get purge bcmwl-kernel-source


[sudo] password for engineer: 


E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)


E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


engineer@engineer:~$



```

---

### Post by jahern on 2014-05-19
actually that worked!  but it does say:

```
the following package was automatically installed and is no longer required
dkms
use 'apt-get autoremove' to remove them.
```

before going into the install of the updates I downloaded with apt-get update.  that seems to be working.  thanks!

---

### Post by wildmanne39 on 2014-05-19
Do not install additional driver and it should stay working.
> the following package was automatically installed and is no longer required
dkms
use 'apt-get autoremove' to remove them.that is just a message saying it is safe to remove that package to save space.

---

### Post by jahern on 2014-05-19
ok, removed dkms and am downloading and installing the rest of my updates.  I think I am solved!  thanks

---

