---
title: "Can't connect to wireless network [URGENT]"
date: 2013-02-15
forum: New to Ubuntu
---

### Post by Pj1989 on 2013-02-15
Hi to everybody

I'm not new to the forum, but I've been away for a long time and now I'm starting my Ubuntu experience all over again. 

I just installed Ubuntu on an external hard drive that I run from my MacBook Pro booting with rEFIt. Yesterday evening I installed it and I even downloaded few programs and everything was ok. 

Today I have absolute needing of the Internet (I'm in a different place) but I cannot connect to any network. The network symbol in the top right corner is "empty" and when I click on it I see the following:

wired network (greyed)
disconnected (greyed)
_____________
VPN connections
       Configure VPN...
       Disconnect VPN (greyed)
_____________
Enable networking (enabled)
_____________
Connection information (greyed)
Edit connections...

I can't see any wireless network in there. 

I know it's a really noobish question, but I can't really figure it out. I'm stucked.

Can anybody help me?

---

### Post by kc1di on 2013-02-15
Hello Pj1989

Could you go to a terminal and issue the following commands then list the output of each ?

```
sudo rfkill list
```
```
lspci
```

Then we may beable to help better. 
P.S. Welcome back to Ubuntu.

---

### Post by Pj1989 on 2013-02-15
```
rfkill list
0: hci0: Bluetooth
              Soft blocked: no
               Hard blocked: no

```

Lspci
[https://www.dropbox.com/s/z5kkxqe415zzxw5/Foto%2015-02-13%2011%2055%2000.jpg](https://www.dropbox.com/s/z5kkxqe415zzxw5/Foto%2015-02-13%2011%2055%2000.jpg)

I'm sorry but I'm writing from my phone, so I can't copy/paste :s

Thanks

---

### Post by kc1di on 2013-02-15
That wireless card is a bit of a problem at times. 

but [here is a thread]("http://askubuntu.com/questions/218986/how-to-fix-a-broadcom-43224-rev-01-in-ubuntu-12-10-running-on-a-macbook-pro") on Ask Ubuntu that may lead to a solution.
Hope it's of help.

---

### Post by Pj1989 on 2013-02-16
I've read the link you have posted. Can you please help me a little more step-by-step? I'm really a beginner with the terminal and the other stuffs.

thank you very much

---

### Post by kc1di on 2013-02-16
> **Pj1989 said:**
> I've read the link you have posted. Can you please help me a little more step-by-step? I'm really a beginner with the terminal and the other stuffs.

thank you very much
Will Try
first thing we need to do is run the following command in the terminal and post the out put you get here.

```
lspci -nn | grep 0280
```
you can just copy and paste it in a terminal if you want.

---

### Post by Pj1989 on 2013-02-16
Here the output 
```
03:00.0 Network controller [0280] :  Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01)
```

---

### Post by kc1di on 2013-02-16
Ok now in a terminal run the following commands one at a time.

Then see if wireless will work?

```
sudo apt-get install linux-headers-generic
    sudo apt-get install --reinstall bcmwl-kernel-source
    sudo modprobe wl
```

again you can copy and past them 
if you get any error messages post them here.

---

### Post by Pj1989 on 2013-02-17
the first command gives me this output:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-headers-3.5.0-23 linux-headers-3.5.0-23-generic
The following NEW packages will be installed:
  linux-headers-3.5.0-23 linux-headers-3.5.0-23-generic linux-headers-generic
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 13.1 MB of archives.
After this operation, 70.0 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://it.archive.ubuntu.com/ubuntu/ quantal-updates/main linux-headers-3.5.0-23 all 3.5.0-23.35
  Could not resolve 'it.archive.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ quantal-security/main linux-headers-3.5.0-23 all 3.5.0-23.35
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ quantal-security/main linux-headers-3.5.0-23-generic amd64 3.5.0-23.35
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ quantal-security/main linux-headers-generic amd64 3.5.0.23.29
  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.5.0-23_3.5.0-23.35_all.deb  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.5.0-23-generic_3.5.0-23.35_amd64.deb  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_3.5.0.23.29_amd64.deb  Could not resolve 'security.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

thank you very much for your help btw

---

### Post by kc1di on 2013-02-17
Sorry for the delay been a busy weekend.

Try a different mirror the one your using must be down at the moment.

or try again now see if it's back up.

You can change mirrors by going to software center >edit>software sources there is a dropdown that says download from click on it and change the server. then do ```
 sudo apt-get update 
``` try again.

---

### Post by Pj1989 on 2013-02-18
What a noob! Of course it gives me error, I'm not connected to any network. Sadly I haven't any wired connection available at the moment, so I have to wait few days. Thanks anyway... I'll post as soon I can try what you told me. 
By

---

### Post by Pj1989 on 2013-02-24
Ok, after a hard week of work i'm back on this problem. So...
The first command went pretty good. I had to update the repository, but after that everything when fine.
The second command instead gave me something doubt:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 21 not upgraded.
Need to get 1,181 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://mirror.sov.uk.goscomb.net/ubuntu/ quantal/restricted bcmwl-kernel-source amd64 5.100.82.112+bdcom-0ubuntu3 [1,181 kB]
Fetched 1,181 kB in 1s (605 kB/s)              
(Reading database ... 206804 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.100.82.112+bdcom-0ubuntu3 (using .../bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (5.100.82.112+bdcom-0ubuntu3) ...
Loading new bcmwl-5.100.82.112+bdcom DKMS files...
Building only for 3.5.0-23-generic
Building for architecture x86_64
[B]Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
ERROR: Module bcma does not exist in /proc/modules
FATAL: Module wl not found.[/B]
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-23-generic

```

and the third, accordingly to the second command's output, gave me simply
```
**FATAL: Module wl not found.**
```

Do you know what I'm supposed to do now?
Thanks for your help

---

### Post by Pj1989 on 2013-02-24
Nothing to do. I've tried what they told
-here [COLOR=Gray]http://ubuntuforums.org/showthread.php?t=2076412[/COLOR]
-here [COLOR=Gray]http://askubuntu.com/questions/218986/how-to-fix-a-broadcom-43224-rev-01-in-ubuntu-12-10-running-on-a-macbook-pro[/COLOR]
-here [COLOR=Gray]http://ubuntuforums.org/showthread.php?t=1406499
-and here [http://blog.projectz.me/2012/10/21/setting-up-ubuntu-12-10-on-a-macbook-pro/](http://blog.projectz.me/2012/10/21/setting-up-ubuntu-12-10-on-a-macbook-pro/)[/COLOR]

Nothing worked, or I haven't done it correctly. I'm quite desperate, also because it's really boring to have to reboot each time i need to look something on the internet.

---

### Post by kurt18947 on 2013-02-24
> **Pj1989 said:**
> Nothing to do. I've tried what they told
-here [COLOR=Gray]http://ubuntuforums.org/showthread.php?t=2076412[/COLOR]
-here [COLOR=Gray]http://askubuntu.com/questions/218986/how-to-fix-a-broadcom-43224-rev-01-in-ubuntu-12-10-running-on-a-macbook-pro[/COLOR]
-here [COLOR=Gray]http://ubuntuforums.org/showthread.php?t=1406499
-and here [http://blog.projectz.me/2012/10/21/setting-up-ubuntu-12-10-on-a-macbook-pro/](http://blog.projectz.me/2012/10/21/setting-up-ubuntu-12-10-on-a-macbook-pro/)[/COLOR]

Nothing worked, or I haven't done it correctly. I'm quite desperate, also because it's really boring to have to reboot each time i need to look something on the internet.


Not an optimal solution but you could buy a 'works out of the box' adapter.  The adapters I've had good luck with are Netgear's WNA-1100 using an Atheros chip set and two very similar adapters using RealTek's 8192SU chipset;   Dlink DWA-131 or TrendNet TEW-649UB.  There are other excellent choices but those work for me.  The Atheros chipset adapter sometimes benefit from a one line .conf file to disable hardware encryption, using software encryption instead.  I'm using these on AMD & Intel machines, I assume they'd work on a Macbook as well.

There's another nice choice for portables, RTL8188CUs powered nano adapters.  I have an Edimax EW-7811Un.  They only protrude out of the USB port about 1 cm. but the native driver is unreliable.  A driver downloaded from Realtek's site and installed via the install script then blacklisting the native driver has been fine on 12.04 & 12.10.  You just have to rerun the script occasionally if the kernel updates.  It would be preferable to get the came-with-it adapter working but some chipsets simply don't have good support yet.

---

