---
title: "Ubuntu does'nt remembers my screen resolution."
date: 2012-08-08
forum: New to Ubuntu
---

### Post by paichkash on 2012-08-08
hi
when i set my resolution in ubuntu desktop  it works until i reboot it... on reboot i my resolution goes back to auto where the icons are realy big big ..

i have nvidia fx5500 256mb gpu.

NVIDIA Driver Version:173.14.16
i use nvidia utility to to configure the resolution..

i have this issue only with the non root account.. on root account i have now such issue ... that remembers what my settings were.. 
Thanks

---

### Post by paichkash on 2012-08-09
help please i red somewere on ubuntu site (forum/wiki)  that use gksudo nvidia-settings .. i did that but stil my settings after re logging reverts to 1024*768.. i always have to set it manually . please..

---

### Post by NikTh on 2012-08-09
Hi ,
please provide more information by open a terminal (ctrl+alt+t) and paste below commands 
```
cat /etc/lsb-release && uname -r
sudo lshw -C video
sudo lspci -v| grep -iA10 vga 

```Post the results back here. 
Put the results inside [CODE] tags , by highlighting the text and click the [SIZE=3]**#**[/SIZE] symbol on top of message pane.
Thanks

---

### Post by paichkash on 2012-08-11
```
[CODE]r@r-desktop:~$ **cat /etc/lsb-release && uname -r**
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"
2.6.28-19-generic

```[/CODE]

```
r@r-desktop:~$ **sudo lshw -C video**
[sudo] password for r: 
  *-display               
       description: VGA compatible controller
       product: NV34 [GeForce FX 5500]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 bus_master cap_list
       configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
```

```

r@r-desktop:~$ **sudo lspci -v| grep -iA10 vga**
02:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
	Subsystem: Micro-Star International Co., Ltd. Device 911a
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	[virtual] Expansion ROM at f0000000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Capabilities: [44] AGP version 3.0
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

```

hope this gives some clue.. 
thanks

---

### Post by NikTh on 2012-08-11
> **paichkash said:**
> ```
r@r-desktop:~$ **cat /etc/lsb-release && uname -r**
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"
2.6.28-19-generic

```

Hi , 
this gives me the clue that you must upgrade your Operating system. You have a very old and unsupported Ubuntu 9.04. 

Try to upgrade on a newer version . Fisrt backup (copy somewhere) all your important - personal files and then download and install a newer version. 
A supported version. e.g : Ubuntu 12.04 LTS. 
First try (from live session) and see how Ubuntu behavior with your hardware and then proceed to installation. 
Thanks

---

### Post by paichkash on 2012-08-16
:(

i do not like the new ubuntu i tried that and throw away that instantly... 

i realy like this version and upgrade is not possible as i have dialup connection and its unreliable also extreme electricity blackouts here .. every hour...

will appreciate if some one helps me out.. 
also i have mentioned that with root user i have no issue ubuntu remembering the resolution that i set .. its just with this login that i m using (non root) ...

also i have followd the advice in the guide which i linked above ... but no sucess...

---

### Post by paichkash on 2012-08-16
please help :popcorn:

---

### Post by paichkash on 2012-08-20
halp ... police help me:lolflag:

---

### Post by sandyd on 2012-08-20
paichkash, I am sorry, but we do not provide support for distros that are past their EOL date.

If you don't like unity, check out [Use Gnome Classic in Ubuntu 12.04]("http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed")

---

### Post by paichkash on 2012-08-20
^^ ok thanks .. but this "please update to supported version" or "we do not support EOL versoin " thinkgy is like sexuall harrasment ...sorry for being blunt .. 

i am trying this time a version that is not EOL.. got first fatal problem after first boot .. i searched for that issue and came accross many soltuins neither of which worked.. now i am at fresh install  of that os hope this time i do not get error..

btw can anyone tell me some thing that is stable and is not made outdated as quickly as ubuntu ? heard a lot about CentOS ... 
will read about that and try to get a feel of that .as i feel harrassed here at ubuntu forums ..

---

### Post by teward on 2012-08-20
When you're using an EOL release, there's not much you *can* do but upgrade, because its possible your fix was included in there.  So its not harassment, its typical Ubuntu support recommendations.

And define "stable", because Ubuntu is not so grossly out of date if you keep your system updated/upgraded to a supported release :P

---

### Post by paichkash on 2012-08-26
i hve reformated and reinstalled and followed the above guide now issue is solved...

thanks all

---

