---
title: "Amdgou-pro driver breaks installed system"
date: 2018-03-26
forum: New to Ubuntu
---

### Post by droid2bsd88 on 2018-03-26
For my 30th birthday my father help my purchase a Dell Precision Tower 3420 Workstation. Which works fine on all flavors of Ubuntu accept when I try to download AMD/ATI's proprietary amdgou-pro driver package from their Linux driver portal the card in question is the FirePro WS2100.

---

### Post by wildmanne39 on 2018-03-26
*Thread moved to **New to Ubuntu, a more appropriate forum**.*

---

### Post by QIII on 2018-03-26
Hello!

What do you mean by "trying to download"?  Will the driver not download, or will it not work if you try to install it?

That card is a GCN 1.0 card, which has only recently been added to support by the AMDGPU driver (which has to be present to overly AMDGPU-PRO over it).  It is possible that the Ubuntu installer does not yet recognize it as a card for which it should install AMDGPU and may have installed Radeon instead.

Please post the results of 

```
lsmod | grep radeon
```

and

```
lsmod | grep amdgpu
```

which will tell us which module is loaded.

---

### Post by boobz on 2018-03-27
This GPU is not supported by this driver. You have to stay on drivers installed by default, try Oibaf's driver ([https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)) or install Ubuntu 14.04.4 - on Ubuntu 14.04 you can't install new Kernel and Xorg drivers higher than 1.16, cause they're uncompatible with fglrx driver. [https://askubuntu.com/questions/815591/ubuntu-14-04-5-16-04-and-newer-on-amd-graphics](https://askubuntu.com/questions/815591/ubuntu-14-04-5-16-04-and-newer-on-amd-graphics)
Currently it's hard to get good performance with AMD graphic cards on Ubuntu, so if it's used only for network browsing etc. you can just use default drivers and it will work fine. If you broke your system with AMDGPU PRO you should try uninstall it from terminal, look at first answer: [https://askubuntu.com/questions/799515/black-screen-on-boot-after-amdgpu-pro-install-16-04](https://askubuntu.com/questions/799515/black-screen-on-boot-after-amdgpu-pro-install-16-04) . You will find answer in Google if this won't work.
EDIT: I looked again and it's supported from 17.40 version, so maybe try ```
amdgpu-pro-install --compute 
``` or ```
amdgpu-pro-install --px
``` see comments: [https://www.youtube.com/watch?v=jUXcvZ9TAsE](https://www.youtube.com/watch?v=jUXcvZ9TAsE)

---

### Post by QIII on 2018-03-27
> **boobz said:**
> 
Currently it's hard to get good performance with AMD graphic cards on Ubuntu . . .

That's not strictly true.  AMD and Canonical have had a romance going on for many years, so whatever AMD has that will work for Linux gets to Ubuntu first.

The demise of fglrx affects ALL Linux distributions with the more recent X Server versions.  AMD simply stopped work on fglrx because their technology moved on and it did not make good business sense to expend enough resources to maintain an aging driver for aging technology that would only be used by at best some fraction of 2% or so of the PC market.  

So they moved to AMDGPU for Linux with their GCN (Graphics Core Next) GPUs.  If you have a recent release of Ubuntu and a GPU that is compatible with AMDGPU, Ubuntu will load the AMDGPU driver at install time, as 16.04 and later have done for me with my GCN 2.0 GPU.  It is as simple as installing Ubuntu.

AMDGPU-PRO is a proprietary overlay to AMDGPU and that you do have to install, but it is dead simple.

AMD's move to AMDGPU is bumpy for the entire Linux community, but it came as a result of the community's demands for a good-performing and well-behaved open source driver.  This is a "be careful what you wish for" moment for the Linux community.  It will be sorted as those using the older GPUs will decrease in numbers and eventually AMD will just be taken care of at install -- which will chafe NVIDIA to no end.

AMD is moving forward from all the headaches, bad support and poor drivers that they inherited when they bought ATI.  It's like trying to wash off axle grease, but they are getting it done.  Just like we all asked for.

As for a driver from a PPA ... Well, I remember a period of about 2 years when nearly every thread I responded to was from someone complaining about how something changed and the PPA-supplied drivers became a mess because of the hacks that made them work.  No disrespect intended to those who develop those things.  They are trying to get stuff to work.  That's a very difficult task.  But they don't control what the OEM does and they can get caught out by changes.

By the way, as a GCN 1.0 GPU, support under AMDGPU is coming as AMD has time to "back fill" the GPUs before GCN 2.0.  And, as I said, you have to remember that AMD is expending an inordinate amount of resources on a tiny fraction of the market.  It's not like they don't support Linux.  They do.  They are a member of the Linux Foundation.  Per market share point, they are spending a lot more on Linux than they are on Windows.

---

### Post by droid2bsd88 on 2018-04-03
I managed  to get the amdgpu-pro drivers functioning under  Lubuntu No problem

Here is the out put of  lsb_release -a

```
porter@Precison:~/Pictures$ lsb_release -aNo LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.4 LTS
Release:    16.04
Codename:    xenial



```

and the output of dpkg -l amdgpu-pro

```
porter@Precison:~/Pictures$ dpkg -l amdgpu-proDesired=Unknown/Install/Remove/Purge/Hold| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  amdgpu-pro     17.40-492261 amd64        Meta package to install amdgpu Pr
porter@Precison:~/Pictures$ 



```

and last thing is the user permissions 

```
porter@Precison:~/Pictures$ groupsporter adm cdrom sudo dip video plugdev lpadmin sambashare
porter@Precison:~/Pictures$ 



```

---

