---
title: "Problems with the screen: flickering, turning off, and some small black spots"
date: 2023-11-03
forum: New to Ubuntu
---

### Post by muri1234 on 2023-11-03
I have a new laptop (Lenovo Thinkpad T14 Gen 3) since August this year, and I have Ubuntu 22.04.03 installed on it.
 
 
 Unfortunately, it doesn't seem to run quite stably. Various issues with the screen are occurring:
 - The screen flickers (the image shifts, with the upper part remaining normal and the lower half, usually about 6 cm to the right, shifted for a second). There is no clear pattern, but I would say it happens when I have many applications open or switch between them. (this problem occurs now very rare)
 - After a month, there are small spots in the middle of the screen (looks like dirt).
 - Recently, the screen briefly goes black, mostly when I have many applications open and have just switched or am using a web browser. Very often during calls (at least 3 times per hour, super annoying)
 -Very rarely, after the screen goes black, it remains very dim, and I have to restart.

Some additional information:
 - I am regularly asked if I want to send error reports to Ubuntu, so there does seem to be an issue with the software.

 - Previously, I had Ubuntu 20, and it worked pretty well.
 - When restarting the computer, I receive warnings (long list of [0.891396]blacklist: 
```
Probleme blacklisting hash (-13)
 [1.122331]hub 6-0:1.0: config faild, hub doesent have any ports!(err -19)
 /dev/nume0n1p2: clean, 363988/31227904 files, 104577153/124895488 blocks)

```
 is it related?

 
 
 Can you help me with this?

---

### Post by MAFoElffen on 2023-11-05
Sure. 

Please remember, that it is a Forum Policy to post commands and raw output within Code Tags. You might want to edit your first post, so that you can correct that: EDIT > Advanced Editor > Select the text of your output with your mouse > Select the "#" Icon from the extended Toolbar. > Save 

Your Laptop has NVidia Geoforce MX550 GPU, which NVidia says drivers 470, 525, 535 & 545 works with that...

If you could please select Adv Reply, and post the output of these command ran from a terminal session, posted within Code Tags
```

sudo lspci -nnk | grep -A3 -E 'Display|VGA|3D'
apt list nvidia* --installed

```
And I am also curious about what your blacklist errors are that you mentioned that you are getting...
```

sudo grep -i 'blacklist' /var/log/boot.log
journalctl -b -l -g 'blacklist' --no-pager | grep -v '/usr/bin/grep'

```

---

### Post by muri1234 on 2023-11-06
Thanks, here the outputs of the commands:
```

apt list nvidia* --installed

pcilib: Error reading /sys/bus/pci/devices/0000:00:08.3/label: Operation not permitted
04:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Rembrandt [1002:1681] (rev d1)
    Subsystem: Lenovo Device [17aa:50b6]
    Kernel driver in use: amdgpu
    Kernel modules: amdgpu

apt list nvidia* --installed
Auflistung&#8230; Fertig

journalctl -b -l -g 'blacklist' --no-pager | grep -v '/usr/bin/grep'
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: Key type blacklist registered
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Loading compiled-in revocation X.509 certificates
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Revoked X.509 cert 'Canonical Ltd. Secure Boot Signing: 61482aa2830d0ab2ad5af10b7250da9033ddcef0'
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Revoked X.509 cert 'Debian Secure Boot Signer: 00a7468def'
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
Nov 06 09:14:42 muriel-ThinkPad-T14-Gen-3 kernel: blacklist: Problem blacklisting hash (-13)
```

---

### Post by MAFoElffen on 2023-11-06
Go into your UEFI BIOS setting and ensure that SecureBoot is turned off.

I didn't see anything about NVidia showing up in those results... Hmmm... I guess there were various CPU and GPU options for that model.

Edit this Grub2 default file
```

sudo nano /etc/default/grub

```
Change this line
```

GRUB_CMDLINE_LINUX="radeon.si_support=0 amdgpu.si_support=1 radeon.cik_support=0 amdgpu.cik_support=1 amdgpu.dc=1"

```
Save and exit, then do
```

sudo update-grub

```

---

### Post by muri1234 on 2023-11-08
This did not solve the problem:(

---

### Post by MAFoElffen on 2023-11-08
Please show me this:
```

ls /var/crash

```

---

### Post by muri1234 on 2023-11-08
Thanks for helping:)

```
 ls /var/crash
_usr_bin_seahorse.1000.crash  _usr_libexec_tracker-miner-fs-3.1000.crash 
```

---

### Post by MAFoElffen on 2023-11-09
Please mark this thread as solved as those problems have been resolved. That can be doe by selecting the "Thread Tools" link ad marking it as "Solved". 

Then, I would file two bug reports, one for each of those:
```

ubuntu-bug seahorse
ubuntu-bug tracker-minor-fs

```
Then upload each crash file from that directory to their respective bug-report... 

Please post the links to the end of this thread, so I can follow them. If you do continue to have problems with either of those, then post a new thread on which one is a problem.

---

### Post by muri1234 on 2023-11-13
here the first link:
[https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/2043403](https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/2043403)

second link:
[https://bugs.launchpad.net/ubuntu/+source/tracker-miners/+bug/2043404](https://bugs.launchpad.net/ubuntu/+source/tracker-miners/+bug/2043404)

Thanks for helping...

---

