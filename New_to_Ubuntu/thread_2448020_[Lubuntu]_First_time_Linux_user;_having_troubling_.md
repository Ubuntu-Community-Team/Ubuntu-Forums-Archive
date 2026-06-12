---
title: "[Lubuntu] First time Linux user; having troubling booting on an old machine"
date: 2020-07-30
forum: New to Ubuntu
---

### Post by jessej1996 on 2020-07-30
I'll try to be as concise as possible:

I am not very familiar computers - I am working on a PC build, and while I wait for the parts to arrive I've decided to try to bring some new life to a few old computers I have.

The machine is an old dell optiplex, the hard drive was dead so I put a different used HDD in and used Rufus to put Lubuntu 18.04.4 on a flash drive. Installing it on to the HDD seems to go fine, but when I reboot the system from the HDD the screen just freezes on a seemingly random color - the same thing happens when I choose the "try lubuntu" option

I will attach some pictures I took of what happens when booting

[https://ibb.co/x6kjxk3](https://ibb.co/x6kjxk3)
[https://ibb.co/dmsDvj8](https://ibb.co/dmsDvj8)
[https://ibb.co/Bnmg2Yg](https://ibb.co/Bnmg2Yg)
[https://ibb.co/mR614gM](https://ibb.co/mR614gM)

The first time I booted it showed that strange pattern, every time since then it has been just a single color on the whole screen; black, blue, green, orange

Any help would be appreciated friends

---

### Post by Bashing-om on 2020-07-30
jessej1996; Hello - Welcome to the forum

Graphic's driver issue ?
what results with the boot parameter "nomodeset" ?
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

If you reach a GUI with this boot parameter we then see what we can do to install a driver.

[INDENT]there is a process
[/INDENT]

---

### Post by QIII on 2020-07-30
Hello!

How old is the machine?  What are its specifications?  What is the make and model of the GPU?

---

### Post by jessej1996 on 2020-07-30
I shouldn't have started this thread right before I went to work &#128556;
It's a Dell Optiplex - I believe 745. I don't know the specs off hand but I know that it doesn't have a graphics card, just uses the integrated graphics on the CPU

---

### Post by uninvolved on 2020-07-30
Along with nomodeset, as bashing mentioned above, there's 'noapic' that can be selected during the boot process for a live USB. I've seen adding that option get rid of similar installation issues.

---

### Post by guiverc on 2020-07-31
I can't provide much, except in the Lubuntu QA-testing is the following box (cpy, ram, gpu)

```
dell [optiplex] 745 (c2d-6600, 6gb, amd/ati radeon rv516/x1300/x1550)
```

In my experience components in 745 & 755s vary on box (desktop, tower, SFF, USFF), options selected and date of manufacture, but I don't recall any issues on any of the three (745) I used.  I'm only aware of AMD or intel video being used in them.

I would still check the integrity of your install media (unless you already did it).  ie [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)  or it's the *Check disc for defects* option found on the first screen at [https://manual.lubuntu.me/stable/1/1.3/installation.html](https://manual.lubuntu.me/stable/1/1.3/installation.html)  (that manual applies to Lubuntu 20.04 LTS)

---

### Post by jessej1996 on 2020-07-31
Thank you everyone, I tried adding "nomodeset" to the boot sequence and everything is running great now. Cheers

---

### Post by Bashing-om on 2020-07-31
jessej1996; Well -

"nomodeset" is not a long term solution - we do need to find out why the graphic issue exist and correct.

As we now know it is graphics related we now need to know the hardware and what the system thinks.
post back - between code tags:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga
cat /var/log/gpu-manager.log

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT]another step on the road of progress
[/INDENT]

---

### Post by jessej1996 on 2020-07-31
Oof.

I'll see what I can do about this when I'm off work again

---

### Post by jessej1996 on 2020-07-31
Sorry. I'm re-reading through all this and I don't quite understand. What is my next step going to be?

---

### Post by Bashing-om on 2020-07-31
jessej1996;
> 
 I don't quite understand. What is my next step going to be?

Sorry, my poor communications skills.

Next is to paste the requested command's outputs back to this thread.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by jessej1996 on 2020-08-01
I think I understood correctly, this was the output:

```

 *-display:0 UNCLAIMED     
       description: VGA compatible controller
       product: 82Q963/Q965 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller cap_list
       configuration: latency=0
       resources: memory:dfe00000-dfefffff memory:c0000000-cfffffff ioport:ecb8(size=8) memory:c0000-dffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82Q963/Q965 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:dff00000-dfffffff

```

---

### Post by Bashing-om on 2020-08-02
jessej1996; Sorry for the delay

Dual Intel GPUs - I do not know how to deal with this as the driver is included in the kernel.
I hope others here will chime in for advise.

Maybe the log file will shed some light on this ?
```

cat /var/log/gpu-manager.log

```

and that a driver does exist:
```

apt policy xserver-xorg-video-intel

```

[INDENT]sometimes I do wonder
[INDENT][INDENT]other times, I just do not know
[/INDENT][/INDENT][/INDENT]

---

### Post by jessej1996 on 2020-08-02
```

~$ cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/4.15.0-20-generic/updates/dkms
Looking for amdgpu modules in /lib/modules/4.15.0-20-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? no
Is nouveau blacklisted? no
Is nvidia kernel module available? no
Is amdgpu kernel module available? no
Vendor/Device Id: 8086:2992
BusID "PCI:0@0:2:0"
Is boot vga? yes
Error: can't access /sys/bus/pci/devices/0000:00:02.0/driver
The device is not bound to any driver. Skipping...
Vendor/Device Id: 8086:2993
BusID "PCI:0@0:2:1"
Is boot vga? no
Error: can't access /sys/bus/pci/devices/0000:00:02.1/driver
The device is not bound to any driver. Skipping...
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Does it require offloading? no
last cards number = 0
Has amd? no
Has intel? no
Has nvidia? no
How many cards? 0
Has the system changed? No

```

```

~$ apt policy xserver-xorg-video-intel
xserver-xorg-video-intel:
  Installed: 2:2.99.917+git20171229-1
  Candidate: 2:2.99.917+git20171229-1
  Version table:
 *** 2:2.99.917+git20171229-1 100
        100 /var/lib/dpkg/status

```

---

### Post by Bashing-om on 2020-08-02
jessej1996; Ouch -

The ditch gets deeper - does not even see the cards :

Does the kernel know of the cards ?
```

lspci -k | grep -iEA5 'vga|3d'

```

Is a GPU disabled in the firmware ?

[INDENT]Gots to be a reason
[/INDENT]

---

### Post by jessej1996 on 2020-08-02
> **Bashing-om said:**
> jessej1996; Ouch -

The ditch gets deeper - does not even see the cards :

Does the kernel know of the cards ?
```

lspci -k | grep -iEA5 'vga|3d'

```


```

~$ lspci -k | grep -iEA5 'vga|3d'
00:02.0 VGA compatible controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)
    Subsystem: Dell 82Q963/Q965 Integrated Graphics Controller
    Kernel modules: i915
00:02.1 Display controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)
    Subsystem: Dell 82Q963/Q965 Integrated Graphics Controller
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)

```

> **Bashing-om said:**
> 
Is a GPU disabled in the firmware ?[INDENT]Gots to be a reason
[/INDENT]


Not sure how to test this. What exactly does the 'nomodeset' parameter  do to allow me to bypass this?

---

### Post by Bashing-om on 2020-08-02
jessej1996; Hey -

That gets us a little further along.
We know now that the i915 graphic's driver should be used.

So; instead of a "nomodeset" boot parameter - what results when you change to i915.modeset=1.
nomodeset defeats kernel mode setting of which is also ACPI (Advanced Configuration and Power Interface).
We want to work to getting the i915 driver to load.
With 2 Intel cards I can accept that the kernel is confused as to what to do - and I presently do not know what to tell the kernel about it.
However, I am willing to poke at it and see what we can learn.

With - i915.modeset=1 - set; what shows:
```

lsmod | grep i915

```

[INDENT]making progress -
[INDENT][INDENT]slowly
[/INDENT][/INDENT][/INDENT]

---

### Post by jessej1996 on 2020-08-03
i915.modeset=1 results in a black screen

---

### Post by Bashing-om on 2020-08-03
jessej1996; Yuk

Back to doing homework - as I can not see that altering the boot parameter to i915.modeset=0 (zero) will help us in this instance.

[INDENT][INDENT]I shall return
[/INDENT][/INDENT]

---

### Post by jessej1996 on 2020-08-04
Not sure if this helps but i915.modeset=0 did result in a picture and the result of the lsmod command was as follows;
```

~$ lsmod | grep i915
i915                 1282048  0
video                  40960  1 i915
i2c_algo_bit           16384  1 i915
drm_kms_helper        151552  1 i915
drm                   339968  2 i915,drm_kms_helper

```

---

### Post by guiverc on 2020-08-04
This is just FYI information, mainly directed at @Bashing-om

Remembering this question, I used my remaining d745 for a QA-test of Lubuntu 20.04.1
(dell [optiplex] 745 (c2d-6600, 6gb, amd/ati radeon rv516/x1300/x1550))

A `sudo lshw -C video` lists the video card twice on my box; display:0 looks as we'd expect, the display:1 is almost identical (physical id 0.1 instead of just 0 for first & minor differences) and only second is unclaimed.

I think it's a quirk of dell boxes of that era; and the strange video-plug that you connected and split into 2xdvi or 2xvga (pre display port).  (I could have looked at other d755s too I used in testing earlier, but didn't think it sorry). I also looked for a BIOS way to configure video on my 745, but little is provided (nor if mine is using optional card, no option existed to disable it & use an oboard. I don't want to touch that hardware sorry)

---

### Post by Bashing-om on 2020-08-04
jessej1996; Yukkie-poo on me

See guiverc's last - I am flat out dumb on this and do not know what action can be taken to get the driver to load - It's Intel it "just works"; as the driver is included in the kernel.
This again affirms the driver, though available, is not loading:
> 
i915                 1282048  0


Maybe just check and insure that the Intel DDX driver and components are fully installed ?
What shows:
```

dpkg -l xserver-xorg-core xserver-xorg-video-intel libegl1-mesa libgl1-mesa-glx libgl1-mesa-dri

```

[INDENT][INDENT]this but a poke in the dark
[/INDENT][/INDENT]

---

### Post by jessej1996 on 2020-08-04
```

~$ dpkg -l xserver-xorg-core xserver-xorg-video-intel libegl1-mesa libgl1-mesa-glx libgl1-mesa-dri
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  libegl1-mesa:i 18.0.0~rc5-1 i386         transitional dummy package
ii  libgl1-mesa-dr 18.0.0~rc5-1 i386         free implementation of the OpenGL
ii  libgl1-mesa-gl 18.0.0~rc5-1 i386         transitional dummy package
ii  xserver-xorg-c 2:1.19.6-1ub i386         Xorg X server - core server
ii  xserver-xorg-v 2:2.99.917+g i386         X.Org X server -- Intel i8xx, i9x

```
I think I'm at least starting to see what the problem is haha.

---

### Post by Bashing-om on 2020-08-04
jessej1996; Hummm ...

Something is not coming up right in the versioning:
My 18.04 install for comparison
:
```

sysop@x1804mini:~$ dpkg -l xserver-xorg-core xserver-xorg-video-intel libegl1-mesa libgl1-mesa-glx libgl1-mesa-dri
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  libegl1-mesa:a 20.0.8-0ubun amd64        transitional dummy package
ii  libgl1-mesa-dr 20.0.8-0ubun amd64        free implementation of the OpenGL
un  libgl1-mesa-gl <none>       <none>       (no description available)
ii  xserver-xorg-c 2:1.19.6-1ub amd64        Xorg X server - core server
ii  xserver-xorg-v 2:2.99.917+g amd64        X.Org X server -- Intel i8xx, i9x
sysop@x1804mini:~$

```
Where I am running Nvidia graphics with the nouveau driver such that "libgl1-mesa-glx" is not used.

So, What is going on with your install ?
Post back:
```

uname -a
lsb_release -a
apt policy xserver-xorg-core xserver-xorg-video-intel libegl1-mesa libgl1-mesa-glx libgl1-mesa-dri

```

Could it be that we just need to update your system ?

[INDENT][INDENT]Maybe Yes
[INDENT][INDENT][INDENT]could be - not so yes[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jessej1996 on 2020-08-05
```

~$ uname -a
Linux ubuntu 4.15.0-20-generic #21-Ubuntu SMP Tue Apr 24 06:15:38 UTC 2018 i686 i686 i686 GNU/Linux
jesse@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04 LTS
Release:    18.04
Codename:    bionic
jesse@ubuntu:~$ apt policy xserver-xorg-core xserver-xorg-video-intel libegl1-mesa libgl1-mesa-glx libgl1-mesa-dri
xserver-xorg-core:
  Installed: 2:1.19.6-1ubuntu4
  Candidate: 2:1.19.6-1ubuntu4.4
  Version table:
     2:1.19.6-1ubuntu4.4 500
        500 http://us.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages
     2:1.19.6-1ubuntu4.2 500
        500 http://security.ubuntu.com/ubuntu bionic-security/main i386 Packages
 *** 2:1.19.6-1ubuntu4 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main i386 Packages
        100 /var/lib/dpkg/status
xserver-xorg-video-intel:
  Installed: 2:2.99.917+git20171229-1
  Candidate: 2:2.99.917+git20171229-1
  Version table:
 *** 2:2.99.917+git20171229-1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main i386 Packages
        100 /var/lib/dpkg/status
libegl1-mesa:
  Installed: 18.0.0~rc5-1ubuntu1
  Candidate: 20.0.8-0ubuntu1~18.04.1
  Version table:
     20.0.8-0ubuntu1~18.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages
     19.2.8-0ubuntu0~18.04.2 500
        500 http://security.ubuntu.com/ubuntu bionic-security/main i386 Packages
 *** 18.0.0~rc5-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main i386 Packages
        100 /var/lib/dpkg/status
libgl1-mesa-glx:
  Installed: 18.0.0~rc5-1ubuntu1
  Candidate: 20.0.8-0ubuntu1~18.04.1
  Version table:
     20.0.8-0ubuntu1~18.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages
     19.2.8-0ubuntu0~18.04.2 500
        500 http://security.ubuntu.com/ubuntu bionic-security/main i386 Packages
 *** 18.0.0~rc5-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main i386 Packages
        100 /var/lib/dpkg/status
libgl1-mesa-dri:
  Installed: 18.0.0~rc5-1ubuntu1
  Candidate: 20.0.8-0ubuntu1~18.04.1
  Version table:
     20.0.8-0ubuntu1~18.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages
     19.2.8-0ubuntu0~18.04.2 500
        500 http://security.ubuntu.com/ubuntu bionic-security/main i386 Packages
 *** 18.0.0~rc5-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main i386 Packages
        100 /var/lib/dpkg/status


```

---

### Post by Bashing-om on 2020-08-05
jessej1996; Hey hey :)

Newer components are available - maybe these will make the driver compatible ?

Try - Run terminal commands: 
```

sudo apt update
sudo apt upgrade

```

reboot the system, removing the nomodeset parameter.
what results ?

[INDENT][INDENT]maybe Yes
[/INDENT][/INDENT]

---

### Post by jessej1996 on 2020-08-08
Sorry for the wait; booting after update/upgrade booted in to the login screen for a couple seconds before the screen turned blue

---

### Post by Bashing-om on 2020-08-09
jessej1996; Yuk !

> 
booted in to the login screen for a couple seconds before the screen turned blue


All now up-2-date ?
a new:
```

apt policy xserver-xorg-core xserver-xorg-video-intel libegl1-mesa libgl1-mesa-glx libgl1-mesa-dri

```
see now what is installed.

[INDENT][INDENT]if I know better
[INDENT][INDENT]I would do different
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jessej1996 on 2020-08-09
```

~$ apt policy xserver-xorg-core xserver-xorg-video-intel libegl1-mesa libgl1-mesa-glx libgl1-mesa-dri
xserver-xorg-core:
  Installed: 2:1.19.6-1ubuntu4.4
  Candidate: 2:1.19.6-1ubuntu4.4
  Version table:
 *** 2:1.19.6-1ubuntu4.4 500
        500 http://us.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages
        100 /var/lib/dpkg/status
     2:1.19.6-1ubuntu4.2 500
        500 http://security.ubuntu.com/ubuntu bionic-security/main i386 Packages
     2:1.19.6-1ubuntu4 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main i386 Packages
xserver-xorg-video-intel:
  Installed: 2:2.99.917+git20171229-1
  Candidate: 2:2.99.917+git20171229-1
  Version table:
 *** 2:2.99.917+git20171229-1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main i386 Packages
        100 /var/lib/dpkg/status
libegl1-mesa:
  Installed: 20.0.8-0ubuntu1~18.04.1
  Candidate: 20.0.8-0ubuntu1~18.04.1
  Version table:
 *** 20.0.8-0ubuntu1~18.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages
        100 /var/lib/dpkg/status
     19.2.8-0ubuntu0~18.04.2 500
        500 http://security.ubuntu.com/ubuntu bionic-security/main i386 Packages
     18.0.0~rc5-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main i386 Packages
libgl1-mesa-glx:
  Installed: 20.0.8-0ubuntu1~18.04.1
  Candidate: 20.0.8-0ubuntu1~18.04.1
  Version table:
 *** 20.0.8-0ubuntu1~18.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages
        100 /var/lib/dpkg/status
     19.2.8-0ubuntu0~18.04.2 500
        500 http://security.ubuntu.com/ubuntu bionic-security/main i386 Packages
     18.0.0~rc5-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main i386 Packages
libgl1-mesa-dri:
  Installed: 20.0.8-0ubuntu1~18.04.1
  Candidate: 20.0.8-0ubuntu1~18.04.1
  Version table:
 *** 20.0.8-0ubuntu1~18.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages
        100 /var/lib/dpkg/status
     19.2.8-0ubuntu0~18.04.2 500
        500 http://security.ubuntu.com/ubuntu bionic-security/main i386 Packages
     18.0.0~rc5-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main i386 Packages

```

---

### Post by Bashing-om on 2020-08-09
jessej1996; Hummm ...

Shows that the versioning now is consistent :)

what says now the GPU manager ?
```

cat /var/log/gpu-manager.log
lsmod | grep i915

```

[INDENT]gots to be a reason
[/INDENT]

---

